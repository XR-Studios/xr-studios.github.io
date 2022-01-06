# XRS Content Integration Portal

This site is using [docsify](https://docsify.js.org/#/) to convert simple markdown text files into the nice-looking pages you see before you.

The pages are served on the internet via [Github Pages](https://pages.github.com/)

## Markdown
If you're worried about "not knowing markdown", don't be. Markdown files are just .txt files where you can put certain things around your text to quickly format it when being viewed by something that parses markdown (like this website).

Just write your content like you're writing a basic text file and keep [this page](https://www.markdownguide.org/cheat-sheet/) open so you can format it.

## Connecting to the GitHub

First, download either the [GitHub Desktop App](https://desktop.github.com/) for a UI or the [Git CLI](https://git-scm.com/downloads) for command-line usage. The GitHub Desktop App is recommended.

After logging into or creating a GitHub account, ask Ryan or Scott to add your account to the XR Studios group.

When that is done, the left column of your [GitHub homepage](https://github.com/) should be populated with the XR Studios repositories to which you have been given access (namely, the repository for this site)

From the repository for this page, you can make simple or quick edits right in the browser without having to download anything. However, these changes **will not be pushed to the internet** until someone updates the repository conventionally (i.e. not in the browser). For this reason it is highly recommended to not edit any of the files directly from the GitHub.

&nbsp;

To download the repository, mouse over the green `Code` button, select `HTTPS`, and copy the text in the textbox (or click `Open with GitHub Desktop` if using the desktop app)

## GitHub Desktop
1. To download the repository, mouse over the green `Code` button on the GitHub page, and click `Open with GitHub Desktop`
2. When GitHub Desktop opens, on the top tool bar, select `Repository > Pull` to make sure your local files are up-to-date with the GitHub
3. Navigate to the download location and alter/add pages as desired, following the other sections of this guide
4. When you are finished working, fill in the bottom half of the left column, ensuring every file in the left column above is checked. Summarize your changes in the title and give details in the description section.
5. Click "Commit to main" in the bottom of the left column
6. Select `Repository > Push` to submit your modified/new files to the GitHub
7. Start with step 2 whenever editing the site in the future. Not pulling before starting your work will cause problems!

## Command Line
1. To download the repository, mouse over the green `Code` button on the GitHub page, select `HTTPS`, and copy the text in the text box.
2. Open Command Prompt (or Windows Terminal if using Windows 11) and navigate to wherever you'd like the repository to be placed (use the `cd [folder]` command to move and the `dir` command to see folders)
3. Enter the command `git clone [paste the text you copied from GitHub]` to download the repository
4. Navigate inside the repo's folder from your command prompt with the `cd` command
5. Enter `git pull` to make sure your local files are up-to-date with the GitHub
6. Alter/add pages as desired, following the other sections of this guide
7. When you are finished working, enter `git add .`
8. Enter `git commit -m "Summary of Changes"` (incl. quotes)
9. Enter `git push`
10. Start with step 3 whenever editing the site again in the future. Forgetting step 4 will cause problems!

!> Note that if you are using the desktop app, steps 1 and 2 are already covered by clicking **Open with GitHub Desktop** on the GitHub page

## Altering a Page
To add or modify the content on an existing page, simply find that page's markdown file in the /docs/ folders. If you are only altering existing pages, you should not need to worry about folder structure or the _sidebar.md files.

Modify the page(s) as desired then return to step 5 if using the command-line, or step 4 if using GitHub Desktop.

## Adding a new Page
To add a page, simply create a Markdown (.md) file for it in the /docs/ folder structure, ensuring it exactly mirrors the structure of the website (i.e. if you want the page to go under the "Content" section with the Unreal and Notch documentation, create `newPage.md` in `/docs/content/`).

Write your new page as desired, then open the `_sidebar.md` file nearest your new page in the hierarchy (usually in the same folder), and add a link to your page, indented appropriately.

Return to step 5 in the Connecting with GitHub section.