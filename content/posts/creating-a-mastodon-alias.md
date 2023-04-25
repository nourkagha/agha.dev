+++
date = 2023-04-25T01:54:18+02:00
title = "Creating a Mastodon alias"
description = "Create a Mastodon alias using your own custom domain."
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

You can create a Mastodon alias with your own custom domain without having to host your own Mastodon server, thanks to some web magic. It's called an alias because it doesn't change your actual *address*, but it's very useful for identity and discoverability. This means that others can find you on Mastodon (or the wider fediverse) using your alias – a part of your identity that remains unchanged, even if you switch or migrate servers.

Since it uses your own custom domain, your Mastodon alias could be the same as your email address, for example. My Mastodon account is **Nour\@fosstodon.org**, but you can also find my account by searching **nour\@agha.dev**.

To understand how this works, you will need to understand how Mastodon search works, which uses a discovery protocol called [WebFinger](https://webfinger.net). This means that when you search for a username or handle on Mastodon, a WebFinger query is performed which returns a JSON document containing their information.

For example, when you search for **Nour\@fosstodon.org** on Mastodon, a GET request is performed at a WebFinger endpoint which looks like this:

    https://fosstodon.org/.well-known/webfinger?resource=acct:Nour@fosstodon.org

This returns a JSON document which looks like this:

```json
{
  "subject": "acct:Nour@fosstodon.org",
  "aliases": [
    "https://fosstodon.org/@Nour",
    "https://fosstodon.org/users/Nour"
  ],
  "links": [
    {
      "rel": "http://webfinger.net/rel/profile-page",
      "type": "text/html",
      "href": "https://fosstodon.org/@Nour"
    },
    {
      "rel": "self",
      "type": "application/activity+json",
      "href": "https://fosstodon.org/users/Nour"
    },
    {
      "rel": "http://ostatus.org/schema/1.0/subscribe",
      "template": "https://fosstodon.org/authorize_interaction?uri={uri}"
    }
  ]
}
```

To create a Mastodon alias, it involves a simple trick, and all you have to do is host a WebFinger endpoint on your own domain at `/.well-known/webfinger`, the same place it lives on your Mastodon server (i.e. fosstodon.org). For a WebFinger query or lookup to be successful, it needs to find this at the root of your website as a JSON formatted document containing your profile information to be returned.

You can visit this URL and you will find that it returns the same JSON document above:

    https://agha.dev/.well-known/webfinger
    
When you search for **nour\@agha.dev** on Mastodon, a WebFinger lookup is done on the `agha.dev` domain, which finds my Fosstodon account or profile information, and leads to my Fosstodon profile being returned as a result.

Other people can now find me by the same identity and address I use for my email and don't need to know or memorize what server I'm on or instance I decide to migrate to, because the alias is the same. If I need to migrate to another Mastodon instance, I will just need to update the JSON document on my website at `/.well-known/webfinger` with my new instance and Mastodon username.

If you would like to get your own alias set up, I would highly recommend the [Masto Guide](https://guide.toot.as/guide/use-your-own-domain) for this, which makes things very easy by allowing you to interactively fill your information in the placeholder fields.

After I had my alias set up, I decided to take things a step further. Instead of only being found with my custom alias through Mastodon search, I also wanted a way to be able to externally link my account to people outside Mastodon while using my custom domain for consistency. For example, visiting https://agha.dev/@nour would redirect to my Mastodon profile at https://fosstodon.org/@Nour.

There are a lot of ways to do URL redirects, and since my website is hosted on Netlify, this is easily achievable with their powerful and flexible [redirects and rewrites](https://docs.netlify.com/routing/redirects).

This was done by adding these lines to my `netlify.toml` file to create an HTTP 302 redirect:

```toml
[[redirects]]
  from = "/@nour/*"
  to = "https://fosstodon.org/@Nour/:splat"
  status = 302
  force = true
```

By using `*` as a wildcard after `agha.dev/@nour/`, I've not only created a redirect to my Mastodon profile, but also to my posts, since any input there will get appended to `https://fosstodon.org/@Nour/`. You can try this here: https://agha.dev/@nour/109599984030559230
