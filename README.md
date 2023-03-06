# Online Resume with Markdown, Hugo, and GitHub Pages

# Purpose
This tutorial will show you how to use a static site generator with GitHub Pages to host a Markdown-formatted resume online.

## Why should I follow this guide?
Using Markdown, GitHub, and a static site generator for your resume is easier to manage for you, the writer, and for others, the audience. This process promotes fast and frequent updates, catalogues of each change, and instant access to the latest version. Each of these ideas are taken from Andrew Etter's book, Modern Technical Writing (linked in [More Resources](#more-resources)), where they're described in more detail.

### It's easier for you to update
Etter emphasizes using Markdown for living documents, such as a resume that you'll continually be updating with new experience and skills. Consider a PDF resume, for example: as you make edits to it, whether adding new items or fixing typos, every version of the document that you've uploaded or sent elsewhere becomes outdated. Using a more dynamic format (in this case, a Markdown document hosted online) ensures that your resume is always consistent, no matter where and when it's accessed. The time it takes to make and publish these changes is similarly fast. Additionally, using version control software to manage your resume means you have a record of each change you make. All of your old resumes are stored in one place (the GitHub repository), along with your self-authored summaries of what you changed from one version to another.

### It's easier for others to view
Hosting your resume online can get you better exposure to employers. Employers can reference your resume at any time without having to request or download extra files, and because of where it's hosted, they'll always see your latest changes. Furthermore, this resume format is a great opportunity to show your technical skills in Markdown, web development, and version control. This demonstrates curiosity and willingness to learn about various computer science concepts, which is attractive to employers!

# Prerequisites
- A resume formatted in Markdown
    - See [More Resources](#more-resources) for an interactive Markdown tutorial.
- A GitHub account
- The latest version of the [Git command line interface](https://git-scm.com/downloads) installed
- The latest version of [go language](https://go.dev/doc/install) installed
- A command line application, such as Terminal or Git Bash

# Instructions

## Make your website's repository
Your **repository** is where you'll store all of your files, including your Markdown resume, any assets it uses, and any source code you use for your website. We will use GitHub to make an empty repository.

1. Log into your GitHub account.
2. Click the green "New" button. (add diagram here)
3. Configure your repository.
    - Your repository can have any name you'd like! You can rename it at any time.
    - Your repository can be either public or private. As implied by the names, all files and changelogs in a public repository can be seen by anybody, whereas those in a private repository can only be seen by you.
    - You can safely ignore the other options on this page.
4. Click "Create repository" and officially create your new repository!

## Put your repository on your local computer
To add files to our repository, we need a copy of it on our local computer. Using Git, we can make changes on our local computer, then upload the updated repository's contents back onto GitHub so the changes can be accessed from anywhere. Copying a repository to make changes to it from a different computer is called **cloning**.

>Note: **Git** is the name of the version control system; **GitHub** is a specific software used to manage Git repositories. Whenever we use the command line, that's **Git**; whenever we use the website, that's **GitHub**.

5. Copy the link to your GitHub repository.
    - This will usually follow the format `https://github.com/[your GitHub username]/[your repository name]`.
    - You can also find a link on your repository's page, under **Code** > **Local** > **HTTPS**.
6. Open the directory on your local computer where you want to store your repository.
7. Open your command line application in this directory.
    - For Windows users, the native Windows command line applications will not work with these instructions. You can use Git Bash, which comes with Git for Windows.
    - You can find a short introduction to common commands in [More Resources](#more-resources). The two most important ones for this step are:
        - To make sure you're in the right directory, run the command `pwd` (print working directory). This will output the path of the directory you're in.
        - To move directories, run the command `cd [directory path]` (change directory). This will change locations to whichever path you specify.
        
8. Run the command `git clone [your repository link]`.
    - This creates a new folder named after your repository.

## Create your Hugo site
Hugo is a static site generator that can automatically create all the resources you need to deploy your website. For a more detailed tutorial on getting started with Hugo, see [More Resources](#more-resources).

9. Run the command `cd [your repository name]` in your command line application.
10.

## Deploy and test locally

## Publish to GitHub Pages

# More Resources
- [Interactive Markdown tutorial](https://www.markdowntutorial.com/)
- [Command line cheat sheet](https://www.git-tower.com/blog/command-line-cheat-sheet/)
- [Hugo quick start guide](https://gohugo.io/getting-started/quick-start/)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS) ($5.26 on Amazon)

# Authors and Acknowledgements
This tutorial was written by:
- Mia Battad
- Jiehao Lai
- Yash Vyas
- Yirong Wang

With acknowledgements to:
- Garen Torikian ([gjtorikian](https://github.com/gjtorikian) on GitHub), creator of the interactive Markdown tutorial
- Tobias Günter, author of the command line cheat sheet
- Shohei Ueda ([peaceiris](https://github.com/peaceiris) on GitHub), creator of the `gh-pages.yml` file for deploying with GitHub Action

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
