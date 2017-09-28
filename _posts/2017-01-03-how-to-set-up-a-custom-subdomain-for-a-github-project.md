---
title: How To Set Up a Custom Subdomain For a GitHub Project
layout: post
tags: [til]
---
[GitHub Pages](https://pages.github.com) are an excellent way to quickly create
and serve up static web content -- create a new repository, push an index.md,
and enable Github Pages in the repository settings. The documentation on how to
set up a custom subdomain for a particular project can sometimes be confusing.

To do so, you'll need to do three things:

* Pick a custom subdomain -- we'll use `til.tense.io` for this example

* Add a CNAME file to the root of the project you'd like to serve up with GitHub
  Pages. Mine looked like this:

  ```
  til.tense.io
  ```

* Add a CNAME record with your DNS provider to direct requests to the subdomain
  to your user or organization's GitHub subdomain, depending on whether the
  project is owned by a user or organization. In order to create
  `til.tense.io`, I added a record for `tense.io` that looked like this:

  |name |  type |    TTL    |        Data                               |
  |-----|-------|-----------|-------------------------------------------|
  | til | CNAME | 5 minutes | your-username-or-organization.github.com. |


Once your DNS record has propagated, you should be able to navigate to your
subdomain and see your new Jekyll-powered GitHub Pages website.

