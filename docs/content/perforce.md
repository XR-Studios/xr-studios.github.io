# Using Perforce For Content Delivery and Version Control

![logo](../../img/p4v/flowchart.png)

XR Studios uses **Perforce** for Unreal Engine content delivery and version control. Perforce provides a single solution for sharing large files, backups, maintenance, and collaboration with XR Studios. It replaces the need to manually send many large, complex files back and forth via email or link sharing, and acts as a method for both XR Studios and external partners to work on project files simultaneously. Additionally, Perforce allows for "versioning" of files and file history (similar to tools like Git), allowing for us to rollback changes if necessary.

The steps for integrating your project with Perforce are outlined below:

?> Note that the below screenshots were done on Windows and in P4V's Dark Mode. Your P4V interface may look slightly different.

## 🗃️Getting our Templates from Perforce

### 1: Download and Install Perforce

![P4V download page](../../img/p4v/step1a.png ':size=50%')

To utilize Perforce, you will need to download **Helix Visual Client** (or **P4V**), which is the visual interface for using Perforce. You can download [Helix Visual Client (P4V)](https://www.perforce.com/downloads/helix-visual-client-p4v) from Perforce's website.

?> For Windows users, we recommend installing via the EXE installer over the MSI installer.

When you run the P4 installer, you should see the following screen, asking which apps to download. You should only need Helix Visual Client (P4V) and no other apps, so uncheck everything else. From here, installation should finish.

![P4V download page](../../img/p4v/step1b.png ':size=50%')

?> If you are comfortable using a terminal, you can also use the [command-line interface (P4)](https://www.perforce.com/downloads/helix-command-line-client-p4) for tracking your work. However, P4V tends to be easier to use, so we recommend using that.

### 2: Connect to the Depot

![P4V login window](../../img/p4v/step2a.png ':size=50%')

Once P4V has been installed, launch it and you will be greeted by the above window. From here, you will need to input the following information:

-   **Server:** This should always be _ssl:perforce.xrstudios.live:1666_
-   **User:** This should be the username provided to you by XR Studios, typically along the lines of _{project-name}-collab-user-{number}_ (for example, _cheese-collab-user-1_). If only one user was provided, there won't be a number after the _collab-user_ part of the username.
-   **Workspace:** Leave this blank when initially logging in; once you create a workspace you can optionally populate this when logging in to switch to a given workspace immediately.

Once this done, hit "Ok". You may get a message about trusting the connection; click "Trust this connection". From here, you will be asked to input the password given to you by XR Studios. Once entered, you will be connected to the server, and should see something like this:

![P4V main screen](../../img/p4v/step2b.png ':size=50%')

...with a view of your depots on the left (which should only be one, named after the project name) and your files/pending changes on the right. If you open up the project depot using the arrows, you should see a **dev** folder containing our Unreal Engine 5.1 Template.

If the username or password do not work, or you don't see the template anywhere, reach out to *cts@xrstudios.live* and will help you get things figured out!

### 3: Create a New Workspace

![P4V workspace tab](../../img/p4v/step3a.png ':size=50%')

To be able to pull down our template and begin making edits, you need to create a **workspace** in P4V. On the left side of the screen, right beside the _"Depots"_ tab, you'll see a _"Workspaces"_ tab - click on that, and you'll be brought to the workspace view.

From here, you should be able to create a new workspace by going into the dropdown menu at the top of the workspace view and selecting _"New Workspace"_:

![Workspace view dropdown](../../img/p4v/step3b.png ':size=30%')

You should then be greeted by the following menu:

![Workspace creator](../../img/p4v/step3c.png ':size=50%')

From here, you will need to fill out the following things:

-   **Workspace name:** The name you want your workspace to be. This is up to personal preference; P4V also typically autofills this field. However, you can name it anything you like. The XR Studios-preferred structure is _username_computername_projectname_, so you can follow that if you'd like.
-   **Workspace root:** This is the physical file location where your workspace will be on your computer. This autofills to be in your user's Perforce directory, but can be placed anywhere you like as long as it has sufficient storage.
-   **Stream:** This is the stream that your project wll be using; you will need to click the "Browse" button and select the _dev_ stream!

Leave the rest of the settings as default, then click "OK", and your workspace will get created on your computer.

### 4: Syncing the Template Files to your Workspace

![Getting latest revision creator](../../img/p4v/step4.png ':size=50%')

To pull the template from the remote depot to your local workspace, you can click _"Get Latest"_ from the shelf, or right-click your workspace folder and selecting _"Get Latest Revision"_, then wait for the files to finish syncing.

From here, you should now have a copy of the template on your computer. You can begin working on your project in the template, which will be located on your computer in the workspace root you supplied in Step 3. An easy shortcut to getting there is right-clicking on your workspace folder, then going to _"Show In" → "Show In Explorer"_, which will open a window to the folder.

!> Make sure NOT to move the directory from its current location - Perforce workspaces aren't able to be moved! If you want to create a different directory for the files, create a new workspace using the steps above.

## 📝Working with the Content (The Workflow)

Depending on the type of project file supplied, please read through the relevant information about the working with the template scene files in more detail:

-   [Unreal Engine](docs/content/unreal.md)
-   [Notch](docs/content/notch)

When you want to make changes to a file in Perforce, you typically start by "checking out" the file; i.e., you tell Perforce that you're going to edit the file on your local machine. You can then make changes to the file and save your changes locally without affecting the existing item on the server. If you want to add or delete new file, you can also "mark for add" or "mark for delete", respectively. Lastly, if you make changes to a file but want to undo them, Perforce has an option to "revert" the file to what's currently on the server.

?> In P4V, there is also an option called "Reconcile Offline Work...", which will check your local files against the server's files and automatically add / delete / check out any files that are different. Use this feature before submitting to verify everything that's needed in the changelist is there. <br> ![Reconcile offline work](../../img/p4v/reconcile.png ':size=50%')

Any changes you make are then stored in a _changelist_, which is a collection of changes that you want to submit to the Perforce server. You can create multiple changelists, allowing you to work on different changes simultaneously without interfering with each other. You view any changelogs under the _"Pending"_ tab (if you do not see this option in P4V, go to _View → Pending Changelists_). Use this as a tool to confirm you're editing all the correct / necessary files.

![Changelist tab](../../img/p4v/changelist.png ':size=100%')

Once you have completed your changes, you will then submit the changelist to the server. To do this, you can right-click on a changelist and click _"Submit"_, or click _"Submit"_ in the top menu.

![Submit locations](../../img/p4v/submit.png ':size=100%')

Doing this will pull up the following dialog box. From here, you can add a comment and review all the files in the changelist. Once this is all confirmed, you can click the _"Submit"_ button at the bottom, which will submit the content to the server. When this happens, the server performs several checks to ensure that the changes don't conflict with any other changes that have been made to the codebase. If there are no conflicts, the changes are accepted and become part of the main project. Others can then update their local copies of the project to include the changes made in the submitted changelist.

![Submit locations](../../img/p4v/submit-changelist.png ':size=50%')

?> You should submit updates regularly throughout your content creation process. It's good practice to get into the habit of submitting updates after completing small milestones, often multiple times per day. This is useful because:<br>**1.** Each revision (changelist) acts like a backup, meaning you will still have your work in case of a computer crash, or you need to restore a previous version of your project.<br>**2.** Each revision also requires a comment of what work was done, meaning work can easily be tracked between revisions.
