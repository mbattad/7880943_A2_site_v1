# README

# Purpose
This tutorial will show you how to use a static site generator with GitHub Pages to host a Markdown-formatted resume online.

## Why should I follow this guide?
Using Markdown, GitHub, and a static site generator for your resume has two main advantages, described in more detail by Andrew Etter in his book, Modern Technical Writing (linked in [More Resources](#more-resources)).

### It's easier for you to update
Etter emphasizes Markdown for living documents, such as a resume that you'll continually be updating with new experience and skills.

### It's easier for others to view
Hosting your resume online can get you better exposure to employers. Employers can reference your resume at any time without having to request or download extra files. Furthermore, this resume format uses technological tools like Markdown, static site generators, and GitHub version control. This demonstrates curiosity and willingness to learn about various computer science concepts, which is attractive to employers!

# Prerequisites
- A resume formatted in Markdown
    - See [More Resources](#more-resources) for an interactive Markdown tutorial.
- A GitHub account
- The latest version of [go language](https://go.dev/doc/install) installed

# Instructions

## Installation

## Setup

## Deployment

### Local Deployment

### Publishing to GitHub Pages

## Troubleshooting

# More Resources
- [Interactive Markdown tutorial](https://www.markdowntutorial.com/)
- [Hugo quick start guide](https://gohugo.io/getting-started/quick-start/)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS) ($5.26 on Amazon)

# Authors and Acknowledgements
This tutorial was written by:
- Mia Battad
- Jiehao Lai
- Yash Vyas
- Yirong Wang

With acknowledgements to:
- Shohei Ueda ([peaceiris](https://github.com/peaceiris) on GitHub) for providing the `gh-pages.yml` file for deploying with GitHub Action

# FAQ
## Why does GitHub Pages show me a 404 Not Found error?
There are three possible reasons GitHub Pages may show you a 404 Not Found error instead of your website.

### You haven't set `baseURL` in `config.toml`
When you initialize your site, Hugo generates a `config.toml` file with options for your website. The `baseURL` option in this file must match the GitHub Pages standard for URLs, or else your GitHub Page won't display your site.

For a user page, set `baseURL` to `https://www.[your GitHub username].github.io`.

For a repository page, set `baseURL` to `https://www.[your GitHub username].github.io/[your repository name]`.

### You haven't published your site with the `hugo` command
The `gh-pages.yml` file looks for a directory named `public` in your source files to display on the GitHub Page. This directory is generated upon running the `hugo` command. Be sure to run this command, then `commit` and `push` the newly generated files to your website's repository. The GitHub Action we added will automatically update the `gh-pages` branch, which GitHub Pages will use to display your website.

### You've set your deployment source setting to a GitHub Action instead of a branch
Although we use a GitHub Action during deployment, the deployment source setting must be set to "branch." The Action in `gh-pages` *creates* the branch that GitHub pages *deploys,* but doesn't perform the deployment itself.

## Can I publish my GitHub page and keep my repository private?
Yes! The page will be publicly available regardless, but you can still host it while keeping the source repository private on GitHub.

# Begin draft
> 1. follow hugo quickstart
> 2. PUBLISH site before committing
> 3. change baseUrl in config
> 4. set up workflow page
> 5. when configuring pages, use BRANCH, not ACTIONS
> 6. set source page to gh-pages
