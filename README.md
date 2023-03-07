# Online Resume with Markdown, Hugo, and GitHub Pages

# Purpose
This tutorial will show you how to use a static site generator with GitHub Pages to host a Markdown-formatted resume online.

## Why should I follow this guide?
Using Markdown, GitHub, and a static site generator for your resume is easier for you, the writer, and for others, the audience. This process promotes fast and frequent updates, catalogues of each change, and instant access to the latest version. Each of these ideas are taken from Andrew Etter's book, Modern Technical Writing (linked in [More Resources](#more-resources)), where they're described in more detail.

### It's easier for you to manage
Etter emphasizes using Markdown for living documents, like a resume that you'll continually be updating with new experience and skills. Most people opt for PDF or other document formats, but those come with a cost: as you make edits to it, whether adding new items or fixing typos, every version of the document that you've uploaded or sent elsewhere becomes outdated. Using a more dynamic format (in this case, a Markdown document hosted online) means your resume is always consistent, no matter where and when it's accessed. The time it takes to make and publish these changes is much quicker as well. Additionally, using version control software to manage your resume gives you a record of each change you make. All of your old resumes are stored in one place (the GitHub repository), along with your self-authored summaries of what you changed from one version to another.

### It's easier for others to view
Hosting your resume online can get you better exposure to employers. Employers can reference your resume at any time without having to request or download extra files, and because of where it's hosted, they'll always see your latest changes. Even better, this resume format is a great opportunity to show your technical skills in Markdown, web development, and version control. This demonstrates curiosity and willingness to learn about various computer science concepts, which is attractive to employers!

# Prerequisites
- A resume formatted in Markdown
    - See [More Resources](#more-resources) for an interactive Markdown tutorial.
- A GitHub account
- The latest version of the [Git command line interface](https://git-scm.com/downloads) installed
- The latest version of [Go language](https://go.dev/doc/install) installed
- A command line application, such as Terminal or Git Bash
- Your text editor of choice
    - If you aren't sure which text editor to use, I recommend starting with [Visual Studio Code](https://code.visualstudio.com/Download). It has syntax colouring and hints for each of the file formats we'll be working with, such as `.toml` and `.md`.
    - Something as simple as the native TextEdit on macOS or Notepad on Windows will work, but won't be as easy to use.

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

>Note: **Git** is the name of the version control system; **GitHub** is a specific software used to manage Git repositories over the cloud. Whenever we use the command line, that's **Git**; whenever we use the website, that's **GitHub**.

5. Copy the link to your GitHub repository.
    - This will usually follow the format `https://github.com/[your GitHub username]/[your repository name]`. You can also find a link on your repository's page, under **Code** > **Local** > **HTTPS**.
6. Open the folder on your local computer where you want to store your repository.
7. Open your command line application in this folder.
    - For Windows users, the native Windows command line applications will not work with these instructions. You can use Git Bash, which comes with Git for Windows.
    - You can find a short introduction to common commands in [More Resources](#more-resources). The two most important ones for this step are:
        - To make sure you're in the right folder, run the command `pwd` (print working directory). This will output the path of the folder you're in.
        - To move directories, run the command `cd [folder path]` (change directory). This will change locations to whichever path you specify.
        
8. Run the command `git clone [your repository link]`.
    - This creates a new folder named after your repository. Whatever you change in this folder, you can synchronize with Git so that those changes appear in your repository on the GitHub cloud.

## Create your Hugo site
Hugo is a static site generator that can automatically create all the resources you need to deploy your website. It's programmed in the language Go, which is where it gets its name (and why we had to install Go as a prerequisite)! For a more detailed tutorial on getting started with Hugo, see [More Resources](#more-resources).

9. Run the command `cd [your repository name]` in your command line application.
11. Run the command `hugo new site [your website name]`.
    - This generates all the files Hugo needs to serve your website, storing them in a folder named after your website. This folder exists inside your repository folder.
10. Run the command `git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke`.
>Note: This adds the theme "Ananke" to your repository as a **Git submodule**, which is a way of linking other repositories inside your original repository. Later, when we get the latest version of our repository from GitHub, we can get the latest version of every **submodule** we've included in it at the same time. If you want, you can pick a theme from [Hugo's many other themes](https://themes.gohugo.io/), but you might have to follow different instructions to use it. I recommend using Ananke until you're more comfortable with Hugo and Git.
11. Open the `config.toml` file in your site folder in your text editor.
12. Add a line to `config.toml` that says `theme = 'ananke'`.
    - If you've chosen another theme than Ananke, replace `'ananke'` with the name of your theme.
13. Change the `baseURL` field to `https://github.io/[your GitHub username]/[your repository name]`.
>Note: This step is crucial to make sure GitHub Pages will properly display your website in later steps!
14. Change the `title` field to whatever title you'd like your website to have.
15. Save your changes to `config.toml`.

## Post your resume
Now that we have the code to generate our static site, let's add our resume to it! Hugo sites have a subfolder where it keeps a site's **contents**, including any Markdown-formatted **posts** you'd like to add to your site.

16. Run the command `hugo new posts/my-resume.md`.
    - This creates a folder called **posts** in the **contents** subfolder of your site, then creates a Markdown document called `my-resume.md`. The Markdown file it generates contains a header with the metadata Hugo needs to properly display the post.
    - You should be in your Hugo site's folder when you run this command, the same folder in which you ran the command to add a theme.
>Note: You may be wondering why we've made a new Markdown file instead of just moving our resume into the **posts** folder. This is because it's much easier to use Hugo's auto-generated metadata header than to add one to our existing file!
17. Navigate to the **posts** folder in a file explorer.
18. Open `my-resume`.md in your text editor.
19. Change the `title` field to the title you'd like your resume post to have!
20. Copy the contents of your Markdown resume into `my-resume.md` directly underneath the header.

## Deploy and test locally
We may want to preview our changes on our own computer before publishing our website. This is especially important if our site is already published and we want to test our changes before they go live! Hugo lets us use a command to host our site on our own computer, that way we can see what it looks like on a web browser before posting it to the internet.

21. Run the command `hugo server -D`.
>Note: `server` is the command to deploy your website using `localhost`, your local computer's IP address. Adding `-D` tells Hugo to include draft posts in the site's content so you can preview them before publishing them.
22. Enter the URL outputted by `hugo server -D` in a web browser. You should see your site, complete with your resume!
    - When you're ready to stop hosting the server, enter `Ctrl+C` in the command line window where you started it.
>Note: This website can change dynamically. You can edit your content or configurations while the server is running, and it'll update immediately to reflect those changes!

## Prepare for publishing
We're almost ready to publish our site, but we have a few more changes to make. We need to make our resume post official, then synchronize our GitHub cloud repository with our local one using three Git actions: **adding**, **committing**, and **pushing**.

23. Open `my-resume.md` in your text editor.
24. Change the `draft` field to `false`.
25. Save your changes to `my-resume.md`.
26. Open the folder called `.github` inside your repository in your file explorer.
27. Create a folder called `workflows`.
28. Create a file in the `workflows` folder called `gh-pages.yml`.
29. Copy the contents of [Shohei Ueda's GitHub Pages workflow for Hugo](https://github.com/peaceiris/actions-hugo#%EF%B8%8F-create-your-workflow) into `gh-pages.yml`.
>Note: A **workflow** file has defines a trigger, and some steps to automatically execute on that trigger. This particular workflow will deploy your website on GitHub Pages whenever you update your repository on the GitHub cloud. I'll describe this in more detail in the next section, when we actually start deploying!
30. Open your command line application.
31. Run the command `hugo`.
>Note: This is the command to build your Hugo site. It generates important files that are necessary for your deploying the site later!

## Set up deployment
We're finally ready to release our website to the world! We'll use GitHub's built-in Pages feature to host our site.

36. Open your repository on the GitHub website.
37. Click the dropdown menu that says **main**.
38. Enter **gh-pages** in the textfield labelled **"Find or create a branch…"**.
>Note: This creates a new **branch** in your repository. A branch is a version of your repository that "branches" off of the **main** code, called the main branch. By adding a branch, you can make changes to your repository without affecting the main code: this is often used to test new features or bug fixes without messing up working code. In this case, we use a separate branch to store extra files that GitHub Pages needs to serve our Hugo site.
38. Go to **Settings** > **Pages** > **Build and deployment** in your repository on GitHub.
39. Set **Source** to **Deploy from a branch**.
40. Set the dropdown menus underneath to **gh-pages** and **/ (root)**.
41. Click **Save**.

## Publish your website!
The **GitHub Action workflow** we added earlier will serve our website on GitHub Pages as soon as we sync our repository!

42. Open your command line application.
43. Move to your repository folder, the folder that contains your Hugo site's folder.
    - If your command line application is still inside your site folder, you can quickly move to its containing folder by running `cd ..`.
44. Run the command `git add -All`.
>Note: The **add** command tells Git which files you want to include in your repository. We started with an empty repository, so we have to add every file from the previous steps. Adding `-all` to the command accomplishes this.
45. Run the command `git commit -all -message "Created a new Hugo site"`.
>Note: The **commit** command saves a set of changes to your local repository, but doesn't sync them to the cloud *yet*. In this command, we add `-all` to specify that we want to include every file with edits in our saved changeset, and we add `-message` to give our changeset a brief summary for future reference. You can replace the message with whatever you'd like, but your commit message should be short and descriptive so you know exactly what you changed in the future.
46. Run the command `git push`.
>Note: The **push** command is what actually syncs your GitHub repository with your local one. You can **commit** as many times as you'd like, but the repository on GitHub won't change until you **push**. A single push can update the repository with many commits.
47. Enter the URL you used in `config.toml` into a web browser!
    - The **Settings** > **Pages** page on GitHub will also show a link to your site on a banner labelled **Your site is now live at [your site URL]**.
    
Congratulations! You should now have a working website with your lovely resume as its first post. If you're having trouble, check the [FAQ](#faq) for troubleshooting tips, or [More Resources](#more-resources) for tutorials from the Hugo team and Shohei Ueda, the author of the `gh-pages.yml` file we used for deployment.

# More Resources
- [Interactive Markdown tutorial](https://www.markdowntutorial.com/)
- [Command line cheat sheet](https://www.git-tower.com/blog/command-line-cheat-sheet/)
- [Hugo quick start guide](https://gohugo.io/getting-started/quick-start/)
- [GitHub Action workflows with Hugo tutorial](https://github.com/peaceiris/actions-hugo#getting-started)
- [Modern Technical Writing by Andrew Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS) ($5.26 on Amazon)

# Authors and Acknowledgements
This tutorial was written by:
- Mia Battad (that's me!)
- Jiehao Lai ([]() on GitHub)
- Yash Vyas ([]() on GitHub)
- Yirong Wang ([]() on GitHub)

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

For a repository page, set `baseURL` to `https://www.[your GitHub username].github.io/[your repository name]`. This is the method the tutorial uses.

### You haven't published your site with the `hugo` command
The `gh-pages.yml` file looks for a folder named `public` in your source files to display on the GitHub Page. This folder is generated when you run the `hugo` command. Be sure to run this command, then `commit` and `push` the newly generated files to your website's repository. The GitHub Action we added will automatically update the `gh-pages` branch, which GitHub Pages will use to display your website.

### You've set your deployment source setting to a GitHub Action instead of a branch
Although we use a GitHub Action during deployment, the deployment source setting must be set to "**branch**." The Action in `gh-pages` *creates* the branch that GitHub pages *deploys*, but doesn't perform the deployment itself.

## Can I publish my GitHub Page while keeping my repository private?
Yes! The page will be publicly available regardless, but you can still host it while keeping the source repository private on GitHub.

## What makes a static site generator so valuable?
A static site generator is so valuable because of its speed. The *static* part of its name comes from the fact that it uses the templates we provide it to generate all of its pages on startup. This means that nobody viewing your site will have to sit through long load times to move from page to page. As soon as the website is live, the browser already has everything it needs!
