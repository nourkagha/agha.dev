+++
title = "Colophon"
description = "The technology and philosophy behind my independent home on the web — from design to privacy, security, simplicity, and performance."
date = "2026-10-12"
lastmod = "2026-10-12"

showDateUpdated = true
showTableOfContents = true
showReadingProgress = true
+++

This website is my **personal and independent home on the web** — a place to share my thoughts, ideas, projects, writing, and experiments. Inspired by the principles of the [IndieWeb](https://indieweb.org), it's a space where I own and control my content, guided by three core principles: **privacy, simplicity, and performance**.

In an internet increasingly dominated by a handful of social media platforms and algorithm-driven feeds, I believe there's immense value in having a space of your own that isn't dependent on any particular platform, its algorithms, policies, or shifting priorities.

## ⚙️ Technology

This site is built with [Hugo](https://gohugo.io), a fast, open-source static site generator particularly well-suited for content-driven websites. Distributed as a self-contained binary, Hugo keeps tooling lightweight and builds fast, without requiring a JavaScript runtime or build toolchain. It also supports [Hugo Modules](https://gohugo.io/hugo-modules), which use Go for dependency management.

The site uses [Blowfish](https://blowfish.page) as its theme, customized with my own [color scheme](https://github.com/nourkagha/agha.dev/blob/main/assets/css/schemes/nour.css) inspired by Dreamscape, alongside additional CSS for styling and visual refinements.

Content is written in [Markdown](https://markdownguide.org), and the site is deployed and hosted on [Cloudflare Pages](https://pages.dev), with its source code maintained on [GitHub](https://github.agha.dev/agha.dev). Availability and uptime are monitored using [Better Stack](https://betterstack.com), with a public [Status](https://agha.dev/status) page providing service status and incident updates.

A custom [`_redirects`](https://github.com/nourkagha/agha.dev/blob/main/static/_redirects) configuration preserves older URLs and provides convenient shortcuts to feeds, social profiles, and other resources.

## 🎨 Design & Typography

### ✨ Dreamscape

The site's visual identity is centered around **Dreamscape**, my custom visual language built around light, atmosphere, and negative space. More than just an aesthetic or fantasy, it's a personal expression of my identity — my personality, character, creativity, and vision — reflecting both who I am and the ideas, values, and content I share.

It consists of two complementary environments, representing two emotional states within the same inner world — one turning inward and the other reaching outward and upward:

- 🌑 **Dreamscape Midnight — In the Dark (Dark Mode):** A deep, quiet, and contemplative atmosphere where cyan light emerges as a soft, luminous glow, illuminating the near-black darkness and evoking introspection, imagination, and inspiration. A private yet expansive inner world for looking inward, exploring dreams, and finding light within the unknown. Its darkness isn't emptiness or despair, but a space for thought, wonder, and endless possibility.
- ☁️ **Dreamscape Dawn — Above the Clouds (Light Mode):** A bright, heavenly, and ethereal atmosphere where the same cyan light expands into an open, boundless sky, evoking celestial beauty, angelic serenity, and an almost divine sense of bliss and transcendence. A feeling of reaching a higher state of being, embracing new horizons, and finding peace, tranquility, and sanctuary beyond the ordinary.

The design uses a restrained palette of near-black (`#0A0A0A`), white (`#FFFFFF`), and electric cyan (`#00CCFF`), with smooth gradients, soft bloom and glow, gentle radiance, atmospheric luminance, and generous open space. The balance between light and dark echoes the harmony found in nature, while the interplay of light, atmosphere, and space creates a serene, immersive, trance-like experience, evoking depth and emotion without unnecessary decoration.

The backgrounds use optimized WebP images with dedicated desktop and mobile compositions. The site supports light and dark modes, with dark mode as the default and automatic adaptation to system preferences.

#### 🩵 Electric Cyan

At the center of both environments is my signature **electric cyan (`#00CCFF`)**, composed of **100% blue, 80% green, and 0% red** (`rgb(0, 204, 255)`). Its maximum-intensity blue evokes electric energy, inspiration, and transcendence, while its strong green component reflects nature, harmony, and grounded serenity. Together, they form a cool, vibrant, and luminous light expressing two deeply connected aspects of who I am: **the dreamer and the guardian**. The dreamer is Dreamscape's guiding spirit and heart, while the guardian provides its steadfast, grounding, and protective foundation.

The **dreamer** represents imagination, intuition, curiosity, wonder, hope, and the courage to envision what could be. An empathetic, innovative creative spirit, always exploring possibilities, seeking inspiration, and looking beyond the boundaries of what already exists. Guided by independent, progressive thought and an idealistic yet pragmatic outlook, the dreamer aspires toward a better future — one shaped by freedom, creativity, knowledge, progress, and the pursuit of human potential.

The **guardian** represents calm strength, serenity, groundedness, stability, resilience, and the determination to protect what matters. A steady, vigilant, and reassuring presence that offers sanctuary and security amid uncertainty, embodying gentle compassion alongside a fierce, chivalrous spirit of protection, loyalty, and unwavering devotion. Guided by purity of intention, courage, humility, and wisdom, its strength is rooted not in aggression or control, but in conviction, understanding, and the resolve to stand for what is right. Beneath its quiet composure lies a profound loyalty to loved ones and an enduring devotion to the people and principles worth safeguarding — a devotion grounded in compassion rather than blind allegiance. Its gentleness is never weakness, nor does its serenity diminish its strength.

Together, the dreamer and the guardian reflect a balance between idealism and pragmatism, freedom and responsibility, imagination and purpose. One envisions a better world; the other provides the grounding and protection needed to nurture that vision and make it possible.

**Electric cyan brings these qualities together in harmony.** Its cool, luminous nature evokes clarity, tranquility, trust, and the comforting light of a sanctuary. Its soft bloom and gentle glow convey serenity and reassurance, while its *electric* intensity introduces a vibrant spark of life and energy, evoking imagination, inspiration, hope, euphoria, and an uplifting sense of transcendence. The result is a balanced light — gentle without being fragile, powerful without being overwhelming, and steadfast without losing its warmth.

This single, continuous light connects Dreamscape's two emotional states of mind. In Midnight, it emerges from within, illuminating imagination and offering comfort in darkness. In Dawn, it expands into luminous openness, embodying transcendence, freedom, and possibility. Throughout both, the guardian remains a quiet, reassuring presence, offering a sense of sanctuary, serenity, and security.

Together, Midnight and Dawn reflect a philosophy of looking introspectively inward, progressively forward, and imaginatively upward — seeking understanding within ourselves, striving toward a better future, and daring to envision what lies beyond.

**The light discovered inwardly in Midnight becomes the light the dreamer rises into in Dawn.**

### 🔤 Typography

Typography uses the self-hosted variable fonts [Inter](https://rsms.me/inter) for general text and [Fira Code](https://github.com/tonsky/firacode) for code. Inter's clean, contemporary design, subtle geometric qualities, and soft, approachable character complement Dreamscape's minimalist aesthetic, while Fira Code provides crisp, readable monospaced typography with programming ligatures.

## 🔒 Privacy

Privacy is a fundamental part of this site's design, not an afterthought.

There are **no advertisements, tracking cookies, or cross-site tracking**. I use [Umami Cloud](https://umami.is) and [Cloudflare Web Analytics](https://www.cloudflare.com/web-analytics) for anonymized, aggregate usage and performance statistics, not for identifying or profiling visitors.

Some optional features, including comments and Webmentions, rely on third-party services. Cloudflare also processes technical information necessary to deliver and secure the site.

You can explore the site's [public analytics](https://agha.dev/analytics) or read the [Privacy](/privacy) page for more details about how data is handled.

## 🛡️ Security

Security is considered throughout the site's configuration, with an emphasis on protecting visitors and minimizing unnecessary exposure.

A restrictive [**Content Security Policy (CSP)**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CSP) is enforced through Cloudflare Pages using a custom [`_headers`](https://github.com/nourkagha/agha.dev/blob/main/static/_headers) configuration. It restricts resource loading to explicitly permitted sources, uses cryptographic hashes for approved inline content, and reports policy violations through [Report URI](https://report-uri.com).

Additional HTTP security headers provide protections such as HTTP Strict Transport Security (HSTS), clickjacking prevention, MIME-type sniffing prevention, and restrictions on browser permissions and referrer information.

The site's security configuration can be independently evaluated using:

- [Mozilla HTTP Observatory](https://developer.mozilla.org/en-US/observatory/analyze?host=agha.dev) (**A+ grade / 100+ score**) — HTTP security headers and browser security best practices.
- [Hardenize](https://www.hardenize.com/report/agha.dev) (**All tests passed**) — Domain, TLS, HTTP, and email security.

## ⚡ Performance & Simplicity

I believe websites should be **fast, lightweight, readable, accessible, and easy to use**.

This philosophy is partly inspired by [Perfect Motherfucking Website](https://perfectmotherfuckingwebsite.com), which demonstrates how much can be accomplished with relatively little.

I see it as a guiding principle rather than a strict set of rules. Simplicity doesn't have to mean sacrificing personality, aesthetics, or useful functionality. Some features inevitably introduce complexity or performance costs, and that's okay when the benefits justify the trade-offs.

**The goal isn't to build the smallest possible website, but to avoid unnecessary complexity and make deliberate choices about what deserves to be there.**

Hugo's static output, Cloudflare's global network, optimized images, self-hosted fonts, and lightweight customizations all contribute to keeping the site responsive and efficient.

The site has achieved near-perfect scores of **99–100 across all four Lighthouse categories** — Performance, Accessibility, Best Practices, and SEO — on **both mobile and desktop**, as measured by [Google PageSpeed Insights](https://pagespeed.web.dev/analysis?url=https%3A%2F%2Fagha.dev%2F), powered by [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview).

## 🌐 The Open Web

I believe the web should remain open, decentralized, and accessible to everyone.

Social media platforms can be useful for discovering content and connecting with others, but they shouldn't be the only way to publish, share, or participate online.

This site embraces that philosophy by supporting [RSS](https://agha.dev/rss) for following content without relying on algorithms, [Webmentions](https://www.w3.org/TR/webmention/) through [Webmention.io](https://webmention.io) and [Bridgy](https://brid.gy) for interactions across the web, and comments through [Giscus](https://giscus.app) and GitHub Discussions.

These features help connect this independent space to the wider internet without making any single social platform its center.

## 💻 Source Code & Credits

The [source code](https://github.agha.dev/agha.dev) is publicly available under the [MIT License](https://github.com/nourkagha/agha.dev/blob/main/LICENSE).

Original visual assets, including Dreamscape artwork, images, logos, and illustrations, are **all rights reserved** unless otherwise stated and may not be reused without prior permission. Third-party assets remain subject to their respective licenses, terms, and attribution requirements.

See [`ASSETS.md`](https://github.com/nourkagha/agha.dev/blob/main/ASSETS.md) for the full visual asset usage policy.

This website wouldn't be possible without the many people who create and maintain free and open-source software.

It's an ongoing personal project, and I'll continue refining it as I learn, experiment, and discover better ways to do things.

**Built with ❤️ and ☕**
