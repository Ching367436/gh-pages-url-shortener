# GitHub Pages URL Shortener

This is a minimal URL shortener that can be entirely hosted on GitHub pages.

[Yay! We got to the top of HN!](https://news.ycombinator.com/item?id=25110879)

<img src="https://i.imgur.com/ZfD7XGt.png" alt="Top of HN" width="240px">

## Demo

1. [nlsn.cf/1](https://nlsn.cf/1) should link to this repo.

1. To add a new short link, add an issue with the title being the link you want
   to shorten (including the `http(s)://`) to
   [https://github.com/nelsontky/gh-pages-url-shortener-db/issues](https://github.com/nelsontky/gh-pages-url-shortener-db/issues).

1. The newly created short url can be accessed via `nlsn.cf/{issue_number}`

## Features

1. Unlike many URL shorteners, this ~~one does not need a database~~ uses a
   "database" in the form of GitHub issues and can be entirely hosted on GitHub
   pages.

1. There is no need for the pound symbol - short URLs look clean like this:
   `nlsn.cf/1` instead of looking like this: `nlsn.cf/#1`.

## How does this work?

_Thanks to @kidGodzilla for the pretty neat explanation
[here](https://github.com/nelsontky/gh-pages-url-shortener/issues/5#issuecomment-728040879)._

> 1. CNAME points URL to `gh-pages` branch
> 2. 404.html handles all requests
> 3. Small javascript snippet fetches a JSON representation of the GitHub issue
>    via the JSON API, and redirects to the issue title, as a URL.
> 4. Profit?

## This is so cool! How can I use this?!

Disclaimer: This method of creating a URL shortener is hacky and not meant to be
reliable or used in production. Do proceed at your own risk!

1. Fork the repo before cloning your fork.
1. If you are using your own domain:
   1. [Set your domain up for GitHub pages.](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
   1. Change the URL in `src/CNAME` to your domain.
1. If you are using GitHub page's default domain i.e. Something like
   `https://<username>.github.io/<repo-name>/`
   1. Delete the `CNAME` file in the `src/` folder.
   1. Change `var PATH_SEGMENTS_TO_SKIP = 0;` at the top of `src/404.html` to
      `var PATH_SEGMENTS_TO_SKIP = 1;`.
      1. This is as GitHub domains have an additional path segment (the repo
         name) after the host name.
1. Create a new repo as a database. (Or you could use your forked repo)
   1. Update `var GITHUB_ISSUES_LINK = "<your-github-issues-link>"` at the top
      of `src/404.html` accordingly afterwards.
1. `npm run deploy`, and your low cost and cool as heck URL shortener will be
   ready for use!

# Featured forks

To feature your fork here, edit this section and open a PR!

- [eexit/s](https://github.com/eexit/s) - Created a bash script that allows for
  shortening of URLs straight on the command line! Check out his script
  [here](https://github.com/nelsontky/gh-pages-url-shortener/issues/49#issue-745134937).
