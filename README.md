# XR Studios - Content Delivery Portal

This repository contains the documents related to our Content Integration Portal, which can be found at [https://xr-studios.github.io/](https://xr-studios.github.io/#/).

## Getting Started

To begin editing the Portal, first download [GitHub Desktop](https://desktop.github.com/) to your machine and use it to clone this repository to your computer. You will also need to [install NodeJS and npm](https://nodejs.org/en/download).

Once you have these steps completed, open up a terminal (Command Prompt, PowerShell, etc.) and run the following commands:
```bash
npm install docsify-cli --global
cd xr-studios.github.io
docsify serve
```

If on Windows, it may yell at you that "execution of scripts is disabled on this system". To avert this, open PowerShell as an administrator and run `Set-ExecutionPolicy RemoteSigned`, then retry.

If successful, this should open a local version at `localhost:3000`.

## Writing the Docs

The Portal uses a framework called [**Docsify**](https://docsify.js.org/#/?id=docsify), which presents Markdown (.md) files to users in a web-friendly and easily-editable way. Documents live in the `docs` folder, with each subfolder (i.e., `content`, `studios`, etc.) representing a different subdirectory in the portal. Each page in a folder represents a page the user sees, so `docs/content/perforce.md` becomes [https://xr-studios.github.io/#/docs/content/perforce](https://xr-studios.github.io/#/docs/content/perforce) on the live website.

Editing the documentation simply involves making changes to the respective .md file. Once you make changes to a .md page, make sure to save it, then visit its respective page on `localhost:3000` to view how they look in the context of the Portal.

There are a number of plugins added to help enhance Docsify; these can all be seen in the `index.html` file in the root of the directory.

For tips for writing in Markdown, consult a Markdown guide such as [markdownguide.org](https://www.markdownguide.org/).