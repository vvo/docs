---
title: Documentation

includes:
  - auth
  - cli
  - continuous-deployment
  - custom-domains
  - ssl
  - redirects
  - form-handling
  - webhooks
  - inject-analytics-snippets
  - versioning-and-rollbacks
  - prerendering
  - github-permissions
  - api
  - errors

search: true

page_class: guides
---

# Introduction

[Netlify](http://www.netlify.com) builds, deploys and hosts your front end.

``` shell
npm install netlify-cli -g
cd my-site-folder
netlify deploy
```

Deploying a new site with Netlify is so simple it fits in a tweet. -->

This is all you need to deploy a static site folder, but Netlify can do much more for you.

For a good example you can look at the [Netlify](http://netlify.com) main page. Feel free to check it out on [Github](https://github.com/netlify/netlify-home) and correct any typos you see.

Anytime we do a push to Github or merge a pull request on that repo, Netlify will automatically do a clean build of the site with [Jekyll](http://jekyllrb.com/) and deploy to the global CDN.
