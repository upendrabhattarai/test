# Welcome to HCBC Platform

Welcome to our Platform guidelines web-page. Here analysts and developers will find guidelines on how to work with our most common environments.

We are developing platforms for each analysis type we have experience with at HCBC.

Go to each analysis-type section to learn how to use our platform.

## Set up the package

Log onto O2 via the command line and check two things (first-time only): 

   * Remove `bcbio` from you `PATH` by commenting the line in your `.bashrc` if you have it
   * Remove any path you load using the R env variables that could be in your `.Rprofile` or `.bashrc`

Go to the [O2 Portal](https://o2portal.rc.hms.harvard.edu/) and select `HMS-RC Application`, then `RStudio Environment`
<p align="center"><img src="../img/O2_portal_page_with_label.png" width="700"></p>

Start Rstudio with using your desired partition, memory, core and time directives. Add these modules to "Modules to be loaded":
  ```
  git/2.9.5  gcc/9.2.0 imageMagick/7.1.0 geos/3.10.2 cmake/3.22.2 R/4.3.1 fftw/3.3.10 gdal/3.1.4 udunits/2.2.28  boost/1.75.0
  ```
   Click "Launch"

<p align="center"><img src="../img/O2_portal_request.gif" width="700"></p>

Open RStudio by clicking on the "Connect to RStudio Server"

<p align="center"><img src="../img/O2_connect_to_RStudio_with_label.png" width="700"></p>

When the session is started, set you library path typing this command in your console Rstudio window in order to be able to load bcbioR:

```
.libPaths("/n/app/bcbio/R4.3.1")
```

Next, load bcbioR with:

```
library(bcbioR)
```

Check the package version of bcbioR using:

```
packageVersion("bcbioR")
```

Make sure the version is **0.3.*** or later.

<p align="center"><img src="../img/Version_check_bcbioR.gif" width="700"></p>

> Note: If you are working in your local environment, install bcbioR with
> ```
> devtools::install_github("bcbio/bcbioR",build_manual = TRUE, build_vignettes = TRUE)
> ``` 

## General Project

Use this [HCBC app](https://hcbc.connect.hms.harvard.edu/content/8cd62872-0ec9-4905-8920-c745d2375758) to set up a project's name. This name will be used for O2, FAS, GitHub and Dropbox. They may be already defined in the Trello card.

This set up needs [bcbioR](https://github.com/bcbio/bcbioR) and [usethis](https://usethis.r-lib.org) packages. If you are working on the O2 Portal `usethis` is within `/n/app/bcbio/R4.3.1`, so you will not need to install it. Also, `usethis` is a dependency of `bcbioR`, so if you are working locally it should have come along with the download of `bcbioR`.

### Create the Rstudio project

Assign the path that you will be using as the path for your project to the object `project_path` into the `PIs` space on O2:

```
project_path <- "/n/data1/cores/bcbio/PIs/PI_name/lastname_postdoc_rnaseq_human_heart_hbc00000"
```

Now, we will need to create a directory using this path to put our analysis in. If this directory already exists, then you can skip this step. The directory creation can be done with this command:

```
dir.create(project_path)
```

Now, we can open a Rproject for our analysis in this path using:

```
usethis::proj_activate(project_path)
```

> Note: This will restart the session in the project directory. This restart will clear the `.libPaths("/n/app/bcbio/R4.3.1")` and `library(bcbioR)` that we used earlier, so we will need to re-do them in the following steps. 

### Setting up your workspace

We will now add the `.libPath()` that is appropriate for our type of analysis. You can use the table below to determine which `.libPath()` is appropriate for your analysis:

| Type of Analysis | `.libPath()` command |
|:---:|:---|
| Bulk RNA-seq| `.libPaths("/n/app/bcbio/R4.3.1_rnaseq")` |
| Single-cell RNA-seq | `.libPaths("/n/app/bcbio/R4.3.1_singlecell")` |
| ChIP-Seq | `.libPaths("/n/app/bcbio/R4.3.1_chipseq")` |
| CellChat | `.libPaths("/n/app/bcbio/R4.3.1_cellchat")` |
| DNA Methylation | `.libPaths("/n/app/bcbio/R4.3.1_methylation")` |


Since our loaded libraries were wiped when we created a new project, we will need to reload `bcbioR`:

```
library(bcbioR)
```

Once again, let's just double check our version of bcbioR to make sure we are using version **0.3.** or later.

```
packageVersion("bcbioR")
```

Next we need to set the library that `bcbioR` will use each time you open up this RStudio project. By using the `bcbioR::use_library()`, you will be adding the path to your project `.Rprofile` and this will be sourced each time when you open the RStudio project.

| Type of Analysis | `bcbioR::use_library()` command |
|:---:|:---|
| Bulk RNA-seq| `bcbioR::use_library("/n/app/bcbio/R4.3.1_rnaseq")` |
| Single-cell RNA-seq | `bcbioR::use_library("/n/app/bcbio/R4.3.1_singlecell")` |
| ChIP-Seq | `bcbioR::use_library("/n/app/bcbio/R4.3.1_chipseq")` |
| CellChat | `bcbioR::use_library("/n/app/bcbio/R4.3.1_cellchat")` |
| DNA Methylation | `bcbioR::use_library("/n/app/bcbio/R4.3.1_methylation")` |

Now, we will use `bcbioR` to set-up the directory structure that we will be using for our analysis using the following command:

```
bcbioR::bcbio_templates(type="base", outpath=".", org="hcbc")
```

### Setting up GitHub and RStudio

Now, we will connect O2 with GitHub. First, check in your Home directory if a `.gitconfig` file exists. ***You should only need to do this once.*** The contents should look like:

```
[user]
	email = your_email@gmail.com
	name = your_GitHub_username
```

Where `your_email@gmail.com` is the e-mail associated with your GitHub account and `your_GitHub_username` is your GitHub user name.

If you do not have a `.gitconfig` file in your Home directory, follow the instructions in the dropdown below to create a `.gitconfig` file. 

<details>
<summary><b>Click here for instructions for making a <code>.gitconfig</code> file</b></summary>
In order to make a <code>.gitconfig</code>, you will need to run the following command:<br>
<pre>
usethis::use_git_config(user.name = "your_GitHub_username", user.email = "your_email@gmail.com")
</pre><br>
You will replace <code>your_GitHub_username</code> with your GitHub user name and <code>your_email@gmail.com</code> with the e-mail associated with your GitHub account.<br>
<blockquote>
Reminder: If you already have your GitHub username and e-mail associated with your GitHub account in your `.gitconfig` file then you can skip this step.
</blockquote><br>
Click on circular arrow in the top right of the <code>File</code> tab called <code>Refresh file listing</code>. You can check that you have successfully made this <code>.gitconfig</code> file by looking for the hidden file in your home directory. The content should look like:<br>
<pre>
[user]
	email = your_email@gmail.com
	name = your_GitHub_username
</pre>
<hr />
</details>

#### Getting the Git tab

Now, we would like to get the Git tab into our Workspace Browser (where `Environment`, `History`, `Connections` and `Tutorial` tabs are located). We show this transition below:

<p align="center"><img src="../img/Git_pane_RStudio.png" width="1000"></p>


In order to do this we will use the following command:

```
usethis::use_git()
```

This command is the command one would usually use in order to make a commit. However, if we choose to not make a commit and then restart R, it will give us our Git tab in the Workspace Browser. This command should return:

```
✔ Setting active project to "/home/wig051/git_demo".
✔ Initialising Git repo.
✔ Adding ".Rdata", ".httr-oauth", ".DS_Store", and ".quarto" to .gitignore.
ℹ There are 6 uncommitted files:
• .gitignore
• .Rprofile
• DataManagement-Checklist.pdf
• information.R
• README.md
• reports/
! Is it ok to commit them?

1: Yes
2: Negative
3: Not now
```

We do not want to commit these files yet, so select one fo the answers like `Negative`, `No way` or `No`.

> Note: It is unclear why Git gives us three choices. The possible choices are re-arranged each time and have different text. So your option may vary a bit from these, select one fo the appropriate options for **NOT** commiting.

Next, you will be prompted as to whether you want to restart R:

```
A restart of RStudio is required to activate the Git pane.
Restart now?

1: For sure
2: Negative
3: Not now
```

We will need to restart R in order to get the Git tab in our R Studio, so select `For sure`, `Yeah` or some other option for answering in the affirmative. 

#### Creating the first commit

Now, we are going to create our first commit. In order to do this, we need to:

1. Navigate to the Git tab in our Workspace Browser
2. Left-click to check the "Staged" checkboxes next to `README.md` and `.gitignore` to select the files that we would like to add to our first commit
3. Left-click "Commit" in the Git tab
4. Add a message for our commit
5. Left-click "Commit" underneath the textbox where we added the message for our commit
6. Close both Git windows

These steps are summarized in the GIF below:

<p align="center"><img src="../img/Initial_commit.gif" width="1000"></p>

#### Pushing our initial commit

Now we will use the function to push these changes to GitHub with the following command:

```
usethis::use_github(org="hbc",private=TRUE)
```

If you already had a valid GitHub token it will push this repository to the HBC GitHub. However, if your token is expired or this is your first time using GitHub from O2, then you will get this message:

```
ℹ Defaulting to "https" Git protocol.
✔ Setting active project to "/home/wig051/git_demo".
Error in `usethis::use_github()`:
✖ Unable to discover a GitHub personal access token.
ℹ A token is required in order to create and push to a new repo.
☐ Call usethis::gh_token_help() for help configuring a token.
Run `rlang::last_trace()` to see where the error occurred.
```

If this is the case, then you will need to create a new GitHub token, click on the dropdown box below for instructions on how to create a new GitHub token.

<details>
<summary><b>Click here to see how to create a GitHub Token</b></summary>
The first thing we will need to do when setting out GitHub token is to set-up our credential helper. We can do this by going to the left-clicking on the `Terminal` table in the Console Window. You may need to load Git in the Terminal using:<br>
<pre>
module load git
</pre><br>
Then you can provide the following line of code to store your GitHub token for future O2 sessions:<br>
<pre>
git config --global credential.helper store
</pre><br>
This process is summarized in the GIF below:<br>
<p align="center"><img src="../img/Git_config.gif" width="1000"></p><br>
Now that we have let Git know to store our GitHub token, we can create one. In order to create a GitHub token, you will need to run:<br>
<pre>
usethis::create_github_token()
</pre><br>
This will take you to a GitHub Webpage. It may prompt you to sign-in to GitHub. From here, you need to name your token and select an expiration date for your token. Then, scroll to the bottom of the page and left-click <kbd>Generate token</kbd>. These step are summarized in the GIF below:<br>
<p align="center"><img src="../img/GitHub_token_Part_1.gif" width="1000"></p>
Next, you will want to copy your GitHub Token and go back to RStudio. Now we need to set our credentials by using the command:<br>
<pre>
gitcreds::gitcreds_set()
</pre>
Paste in your copied GitHub token and hit <kbd>Return/Enter</kbd>. It should return:<br>
<pre>
-> Adding new credentials...
-> Removing credentials from cache...
-> Done.
</pre>
These steps are summarized in the GIF below:<br>
<p align="center"><img src="../img/GitHub_token_Part_2.gif" width="1000"></p><br>
Now you should have a file called <code>.git-credentials</code> in your Home directory and it should look like:
<pre>
https://PersonalAccessToken:YOUR_GITHUB_TOKEN@github.com
</pre><br>
Where <code>YOUR_GITHUB_TOKEN</code> has been replaced with your GitHub Token. Next, try running the push to the HBC GitHub again with:<br>
<pre>
usethis::use_github(org="hbc",private=TRUE)
</pre>
<hr />
</details>

## Change name in Guideline Push with GUI

## RNAseq

Use this common library path to perform your analysis: `bcbio::use_library("/n/app/bcbio/R4.3.1_rnaseq")`.
* Follow the previous step to set up the [base](#general-project) project if you haven't done it already
* Deploy templates with:

```
bcbioR::bcbio_templates(type="rnaseq", outpath="reports")
```


## scRNAseq

Please, change to this common library path to perform your analysis: 

```
bcbioR::bcbio_templates(type="singlecell", outpath="reports")
```

## ChipSeq

Please, change to this common library path to perform your analysis: 

```
bcbioR::bcbio_templates(type="chipseq", outpath="reports")
```

# bcbioR supported templates

We used `bcbioR` to deploy folders and code to our project directories to improve robustness in our analysis.

You can install `bcbioR` as indicated here: `https://github.com/bcbio/bcbioR/tree/main`

- RNAseq ![](https://img.shields.io/badge/status-stable-blue)
- ChipSeq ![](https://img.shields.io/badge/status-beta-yellow)
- scRNAseq ![](https://img.shields.io/badge/status-beta-yellow)
- CELLCHAT ![](https://img.shields.io/badge/status-draft-grey)
- TEASeq ![](https://img.shields.io/badge/status-draft-grey)
- COSMX ![](https://img.shields.io/badge/status-draft-grey)


# Note
>These materials have been developed by members of the teaching and platform team at the Harvard Chan Bioinformatics Core (HBC) RRID:SCR_025373. 
