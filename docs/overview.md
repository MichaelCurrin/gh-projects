# Overview

## How it works

This project will show your GitHub account's public repos as a statically generated Jekyll site, both locally or on a remote location such as on Netlify. (This _could_ work also with GitHub Actions to run the custom plugins and Jekyll 4. See the [GitHub Actions](https://jekyllrb.com/docs/continuous-integration/github-actions/) section on Jekyll docs - then a schedule parameter could be used for nightly or weekly builds.)

The main limitation that the site has rebuilt in order to get the latest repos and topic tags, but that is easy enough to trigger a new build by hand occasionally on Netlify - command-line `curl` POST requests can even trigger a build. And also this project works best when you have a lot of repos (over 10) and also use detailed but consistent tags based on the use (tool / linter / static site) or tech used (programming language / library / host location).


## Purpose

This project is setup to show repo data for the **current authenticated GitHub user** (i.e. not other users). This is easy with the `jekyll-github-metadata` plugin, but that uses GitHub API version 3 and it does not handle labels. So through some Ruby plugin scripts, this project fetches 100 repos including topics on each and then build a object with topic labels on the outside and repos within.

You can **fork** this project and setup as a Netlify static site which shows your **own** repos and their topic labels. You just have to configure your secret token and the query will get your repos.

When setup as a website, this project can serve the following purposes for the owner:

- Quick reference to **find your own repos** by name and check their stats. With future development, you can find most recent, most starred, etc.
- Group your repos by **topic**.
    - This is is very useful as a portfolio for **job interviews**, since someone can for example see how many Machine Learning, Python and static site projects you have. They can see at a glance what **activity** there is (last updated, how many stars) and optionally click through to see the actual repo.
    - This project is useful for maintaining or searching projects **for yourself**. For example if you want to find all your projects which are hosted on GitHub Pages or Netlify (assuming they are well-labelled). Or all the templates projects.
    - If you want to teach someone about a language or tool and what to show them what you've made, you can guide them to certain topics.
- This project gives you freedom to change the **styling** if you want to present the data in a different way.
- After future development, you can highlight repos or topics to **guide visitors towards**, or help you get to your most important or frequently accesses areas first.

If you want to explore your _private_ repos only, change the `privacy` value in the GraphQL query from `PUBLIC` to `PRIVATE`. Though you might want to just build that locally to avoid sharing that data.
