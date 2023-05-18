+++ 
date = 2023-05-13T17:23:10+03:00
title = "Hosting an MTA-STS policy using Hugo and Netlify"
description = "Create an MTA-STS policy to secure your emails on a domain hosted with Hugo and Netlify."
slug = ""
authors = []
tags = ["security", "email", "web"]
categories = ["security"]
externalLink = ""
series = []
+++

An [MTA-STS](https://emailsecurity.blog/configuring-mta-sts-and-smtp-tls-rpt) (Mail Transfer Agent Strict Transport Security) policy is essential for securing your emails with both encryption and authentication. This helps prevent potential and malicious MITM (man-in-the-middle) attacks which involve interception and tampering during transit through SMTP (Simple Mail Transfer Protocol) used by mail providers. MTA-STS is a fairly new standard which makes email communication much more secure, and has been adopted by [Google](https://security.googleblog.com/2019/04/gmail-making-email-more-secure-with-mta.html) a few years ago and [Microsoft](https://techcommunity.microsoft.com/t5/exchange-team-blog/introducing-mta-sts-for-exchange-online/ba-p/3106386) only a year ago. If you have and use your own domain for email, you will need to create, configure and publish your own MTA-STS policy.

# Creating a policy

My MTA-STS policy is published and can be accessed at `https://mta-sts.agha.dev/.well-known/mta-sts.txt`. For your domain, this similarly requires defining and configuring your policy in an `mta-sts.txt` file under a `.well-known` directory at the root of an `mta-sts` subdomain. In a Hugo repository, for `.well-known` to be at the root of your site, it should go under the `/static` directory at the root of your repository. The `mta-sts.txt` file should have the following contents:

```txt
version: STSv1
mode: enforce
mx: mail.protonmail.ch
mx: mailsec.protonmail.ch
max_age: 604800
```

- The `version` currently adopted is `STSv1`.
- The `mode` can be either `none`, `testing` or `enforce`:
  - `none` disables the policy.
  - `testing` only evaluates the policy without enforcing it and requests reports via TLS-RPT.
  - `enforce` actively enforces the policy and connection security.
- The `mx` values depend on the MX (mail exchange) servers of your mail provider. I use [Proton Mail](https://proton.me/mail) which uses `mail.protonmail.ch` and `mailsec.protonmail.ch` as MX servers.
- The `max_age` value is how long (in seconds) the policy is cached, which is set to a recommended `604800` (1 week).

My site repository is hosted on [GitHub](https://github.com/nourkagha/agha.dev) and I came across this excellent article on [Hosting your MTA-STS policy using GitHub Pages](https://emailsecurity.blog/hosting-your-mta-sts-policy-using-github-pages) and used it for hosting my policy. However, later on I felt that having or maintaining a separate repository (or even branch) just for my MTA-STS policy was not the most efficient approach, and I wanted to keep things as minimal as possible and have everything related to my website in one single repository.

This can be easily done by creating a different branch (`mta-sts`) within my site repository, but having a different branch just to serve one file was also not the most efficient or minimal approach, especially when I already have a `.well-known` directory in my main branch where other files are served under my base domain (such as those needed for my [Mastodon alias](/blog/creating-a-mastodon-alias)).

Placing my `mta-sts.txt` policy configuration file under the `.well-known` directory in my main branch was the best approach, but there was one problem. This would serve it from my base domain `agha.dev` rather than the `mta-sts.agha.dev` subdomain.

# Redirects and rewrites

This is where Netlify [redirects and rewrites](https://docs.netlify.com/routing/redirects), as ever, come in handy. To solve this, defining some redirects and rewrites in my `netlify.toml` file was needed as follows:

```toml
[[redirects]]
  from = "https://mta-sts.agha.dev/.well-known/mta-sts.txt"
  to = "https://agha.dev/.well-known/mta-sts.txt"
  status = 200

[[redirects]]
  from = "https://mta-sts.agha.dev/*"
  to = "https://mta-sts.agha.dev/.well-known/mta-sts.txt"
  status = 302
  force = true
```

The first redirect rule uses the HTTP 200 code and essentially does a rewrite by making use of [rewrites and proxying](https://docs.netlify.com/routing/redirects/rewrites-proxies). This means that when `https://mta-sts.agha.dev/.well-known/mta-sts.txt` is visited, the server responds with `https://agha.dev/.well-known/mta-sts.txt` without changing the URL in the address bar of the browser.

The second redirect rule is a simple HTTP 302 redirect and uses a `*` wildcard. which makes it so that visiting the `https://mta-sts.agha.dev` subdomain always redirects to my MTA-STS policy configuration in `mta-sts.txt`, no matter what's typed after the URL. This is important because this subdomain is not going to be used for serving anything else other than my MTA-STS policy, and due to how the DNS records are configured in Netlify, not having this redirect would instead make the URL serve my website rather than the policy.

If we visit `https://mta-sts.agha.dev/.well-known/mta-sts.txt`, we can see that my policy is successfully returned and served from the correct URL. For short, it can also be accessed at `https://mta-sts.agha.dev`, but the full URL is what mail servers need and look for when checking for an MTA-STS policy.

# DNS records

Lastly, in order to enable MTA-STS and signal that my domain supports it, a DNS record should be defined as follows:

- Name: `_mta-sts.agha.dev`
- TTL: `3600`
- Type: `TXT`
- Value: `v=STSv1; id=1666328180`

The `id` is set as the current time in epoch (UNIX) time (the amount of seconds since 1 January 1970). `1666328180` refers to October 21, 2022, which is the time I created and published my policy. It needs to be unique and updated every time any changes or updates are made to the policy. An [epoch converter](https://www.epochconverter.com) is useful.

To add and enable TLS-RPT (SMTP TLS Reporting) reports for statistics such as successes and failures, I use [Report URI](https://report-uri.com) to collect the reports and have the following DNS record added:

- Name: `_smtp._tls.agha.dev`
- TTL: `3600`
- Type: `TXT`
- Value: `v=TLSRPTv1; rua=mailto:nour-d@tlsrpt.report-uri.com`

This sends reports to `nour-d@tlsrpt.report-uri.com`, which allows the reports and statistics to be displayed in my Report URI dashboard. It can be substituted for one of my emails, but using a service like Report URI collects and aggregates the reports and displays them to be visualized in a nicer way through graphs.

After setting up MTA-STS and TLS-RPT, [Hardenize](https://www.hardenize.com/report/agha.dev) shows that my domain is properly hardened and secured for email.