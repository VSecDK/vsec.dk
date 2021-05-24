# Contributing to VSec

:+1::tada: Thanks for taking the time to contribute! :tada::+1:

The following is a set of guidelines for contributing to the VSec Community.
These are just guidelines, not rules, so use your best judgment and feel free to propose changes to this document.

## Table of Contents

- [Types of community contributions](#contribute-by-creating-or-helping-to-maintaining-community-projects)
  - [Blog](#blog)
  - [Community Projects](#community-projects)
  - [Website](#website)
  - [Events](#events)
 
# Blog

Blog posts are stored in the [/data/blog](/data/blog) directory and are written in [markdown](https://docs.github.com/en/github/writing-on-github/basic-writing-and-formatting-syntax), with [YML front matter](https://jekyllrb.com/docs/front-matter/) at the top for metadata. The `title`, `author`, and `date` properties should be set on all posts.

See this guide for further information: https://guides.github.com/features/mastering-markdown/

**Example post**

```markdown
---
title: 'Security post'
author: Viking
date: '1999-12-31'
---

A thing happened, and this is some intro content about it.

---

I am the rest of the post. Those three dashes above me designate
the cutoff point for the post summary that's displayed on the
/blog index page
```

## Guidelines to keep in mind when publishing a blog

- Posts must be related to Information Security and be relevant to either the VSec members or general public.
- Posts that include material from and/or links to commercial parties must be limited as much as possible.  
  Please consider open source alternatives.
- Posts are reviewed by the VSec Community Board and might be discarded.  
  Remember quality content is more valuable than quantity. 
- Make sure the date in the filename is today's date + name (1999-12-31-topic.md).

# Community Projects

Each project will need an initial approval from the VSec Community Board to be included in the VSec repository, but generally we accept most contributions as long as the project has potential. Be sure to include the following information.

- Short project description

## Issues and Pull Requests

- If you're not sure about adding something, [open an issue](https://github.com/Viking-Security/website/issues/new) to discuss it.
- Feel free to open a Pull Request early so that a discussion can be had as changes are developed.

## Guidelines to keep in mind when publishing a community project

- Projects must be related to Information Security and be relevant to either the VSec community members and/or general public.
- Projects must be open source under the MIT license.
- Projects are reviewed by the VSec community and might be discarded or deleted (with notice) due to quality or being unmaintained.

# Website

The website is hosted on GitHub Pages making it easy to contribute to the site by making simple pull request to any page/post.  
All text on the site is written in markdown and generated into a static site by [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll).  
Nameservers are currently being handle by gratisdns.dk with simple A and TXT/SPF records.  

Stylesheets are all stored in the `/styles` directory.
The styles are based on [Primer](https://github.com/primer/primer-css), the CSS toolkit that powers GitHub's front-end design.

# Events

Want to do a online non-profit event on the VSec Discord server and get the support of the growing Danish InfoSec community, feel free to reach out to @kbodeholt on Discord. As an option we can also help provide a even more professional setup by live re-streaming the event on other streaming services.

## Guidelines to keep in mind when creating an online InfoSec Event

- Events must be related to Information Security and be relevant to either the VSec community members and/or general public.
- Only non-profit events are allowed.
- Only use royalty free music and graphics/overlays that are not under copyright.

## Need Help?
### [Join](https://discord.gg/H6uTh7m) The Discord Server!
Join the Discord server to get connected to hundreds of security aware people
  - Get help regarding any issue you are facing.
  - Make new friends, working in the same area.
  - Find amazing projects to contribute to, or help others with their issues
  
If any of this information confusing, incorrect, or incomplete, feel free to reach out on discord or [open an issue](https://github.com/Viking-Security/website/issues/new) for help.
