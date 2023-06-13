# 🚚 XR Studios - Content Delivery Portal

This repository contains the documents related to our Content Integration Portal, which can be found at [https://xr-studios.github.io/](https://xr-studios.github.io/#/).

## 🏃 Getting Started

To begin editing the Portal, first download [GitHub Desktop](https://desktop.github.com/) to your machine, then log in and clone this repository to your computer. This can be done by:

1. Sign in to GitHub on GitHub Desktop: When you open GitHub Desktop for the first time, you'll be prompted to sign in to your GitHub account. Enter your GitHub username and password and click "Sign in."

2. Clone a repository: After signing in, you'll see the "Clone a repository" window. Click on the "Clone" tab, select the repository you want to work on, choose a local directory for cloning, and click the "Clone" button. This will create a copy of the repository on your computer at the specified location, typically `C:\Users\your_user\Documents\GitHub\xr-studios.github.io`.

You will also need to [install NodeJS and npm](https://nodejs.org/en/download) to your machine.

Though this is up to preference, it's helpful to install [Visual Studio Code](https://code.visualstudio.com/download) to edit the documents (see below).

Once you have these steps completed, open up a terminal (Command Prompt, PowerShell, etc.) and run the following commands:

```bash
npm install docsify-cli --global
cd xr-studios.github.io
docsify serve
```

If on Windows, it may yell at you that "execution of scripts is disabled on this system". To avert this, open PowerShell as an administrator and run `Set-ExecutionPolicy RemoteSigned`, then retry.

If successful, this should open a local version at `localhost:3000`.

## 📝 Writing the Docs

The Portal uses a framework called [**Docsify**](https://docsify.js.org/#/?id=docsify), which presents Markdown (`.md`) files to users in a web-friendly and easily-editable way. Documents live in the `docs` folder, with each subfolder (i.e., `content`, `studios`, etc.) representing a different subdirectory in the portal. Each page in a folder represents a page the user sees, so `docs/content/perforce.md` becomes [https://xr-studios.github.io/#/docs/content/perforce](https://xr-studios.github.io/#/docs/content/perforce) on the live website. Editing the documentation simply involves making changes to the respective `.md` file. Once you make changes to a `.md` page, make sure to save it, then visit its respective page on `localhost:3000` to view how they look in the context of the Portal.

To actually edit the documents, you can use any text editor you'd like (Notepad, Notepad++, Wordpad, etc.). However, for simplicity's sake it's recommended to use [Visual Studio Code](https://code.visualstudio.com/download), as it has plugins built-in for editing Markdown, as well as a good method of viewing the entire file structure (via the "Open With Code" right-click menu option in the project root folder).

There are a number of plugins added to help enhance Docsify; these can all be seen in the `index.html` file in the root of the directory.

For tips for writing in Markdown, consult a Markdown guide such as [markdownguide.org](https://www.markdownguide.org/).

Once you're ready to push changes to the actual site, use GitHub Desktop to commit and push the changes. The steps for doing this are:

1. Make changes: Once you have a repository cloned or created, you can start making changes to the files within the repository directory on your local machine using your preferred code editor.

2. Stage changes: Open GitHub Desktop and you should see the repository you cloned or created listed. On the left-hand side of the window, you'll find a list of the changed files. Review the changes and check the box next to the files you want to include in the commit.

3. Write a commit message: Below the list of changed files, you'll find a text box labeled "Summary (required)." Enter a meaningful commit message that describes the changes you made. Optionally, you can also provide a more detailed description in the "Description (optional)" field.

4. Commit changes: Click the "Commit to main" button (the branch name might vary depending on the repository). This will create a new commit with the selected changes and the provided commit message.

5. Push changes: To push your committed changes to the GitHub repository, click the "Push origin" button. This will upload your changes to the remote repository on GitHub.