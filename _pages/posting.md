---
permalink: /posting/
title: "Posting to VSec"
toc: true

sidebar:
  title: "Archive"
  nav: sidebar-posts
---
Posts are stored in the [_post] directory and are written in [markdown](https://docs.github.com/en/github/writing-on-github/basic-writing-and-formatting-syntax), with [YML front matter](https://jekyllrb.com/docs/front-matter/) at the top for metadata. The `title`, `author`, and `date` properties should be set on all posts. The date should be in the filename in this formatting year-month-day-title.md (1999-12-31-title.md).

See this guide for further information: [GitHub - Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

**Example post**

```markdown
---
title: 'Awesome Security Post'
author: V
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

## Author profile
If you want to have you author profile information shown next to the article you should include author: name in the YML front matter.
Your profile information need to be added to _data/authors.yml and the picture to assets/images/authors/filename.jpg

```markdown
---
Firstname Lastname:
  name   : "Firstname Lastname"
  avatar : "/assets/images/authors/picture.jpg"
  bio    : "My bio"
  location: "City, Denmark"
  links:
    - label: "E-mail"
      icon: "fas fa-fw fa-envelope"
      url: "mailto:mail@mail.com"
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://website.com"
    - label: "LinkedIn"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/in/name"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/name"
---
```