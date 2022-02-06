---
permalink: /about/infrastructure
title: "About VSec Infrastructure"
toc: false

sidebar:
  nav: sidebar-about
---

VSec infrastructure is built to have as small a footprint as possible, that being technical, economical, and environmentally while being easy to manage and to contribute to as community.

## Website
The website is built with GitHub Pages that enables everybody to contribute directly though the GitHub repository.
GithHub Pages is built with static pages using the [Jekyll](https://jekyllrb.com/) static site generator and the free “Minimal-mistakes” Jekyll theme made by [Michael Rose](https://mademistakes.com/).

## CDN
By using a static site and Cloudflare as a CDN resources used to deliver the VSec website should be as [small as possible](https://blog.cloudflare.com/understand-and-reduce-your-carbon-impact-with-cloudflare/
) while still having a security focus.  

## Security
To enable proper web security, Cloudflare is used as a CDN to make it possible to enable DNSSEC, optimize allowed TLS versions, set HSTS and make “transforms” to the [http response headers](https://blog.cloudflare.com/transform-http-response-headers/) so it is possible to enforce Content Security Policie etc.

## Project Management
GitHub also provides good project management tools should that be necessary in the future when [planning](https://docs.github.com/en/issues/trying-out-the-new-projects-experience/about-projects) events.

## Enviromental commitment to technology usage
VSec is commited to as much as possible to only select technology and service providers that focusing on minimizing their enviromental impact.
VSec is a non-profit and all funding that is not used on facilitating the community iself will be given to causes that help support the UN [“2030 Agenda for Sustainable Development”](https://sdgs.un.org/goals) and the 17 goals.