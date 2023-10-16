# Git Large Repositories

![](logo.png)

## Table of Contents

- [Git Large Repositories](#git-large-repositories)
- [Git Large File Storage (LFS)](#git-large-file-storage-lfs)
  - [What is Git LFS?](#what-is-git-lfs)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Usage](#usage)
  - [Benefits](#benefits)
  - [Practical Example](#practical-example)
  - [Troubleshooting](#troubleshooting)
  - [Conclusion](#conclusion)
  - [Resources](#resources)

Having large repositories creates problems that may influence the performance of our work. We can encounter these difficulties while working with remote repositories (cloning, pushing, etc.).

Besides that, platforms that provide various functionalities related to version control might have size limits for files that you want to push.

 - GitHub has file size limits that include a warning for files larger than 50 MiB and a strict prohibition against files larger than 100 MiB. Additionally, GitHub recommends that entire repositories be smaller than 1GB and strongly advises keeping repositories smaller than 5GB, although these recommendations are not strict size limits.
+ GitHub large files: https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github

### We can distinguish two types of big repositories:

1. Repositories with long history (containing a lot of commits over long periods of time)

2. Repositories which include huge binary assets (usually refers to files that contain something	 else than plain text, those can be: compressed files, videos, images, or any other non-text data).

### Solving problems with large repositories:

1. The case with long histories:
 - Sometimes we need keep the history of our repository intact. In that case to solve complications while cloning repository we can clone just n latest commits. We can use:


```bash
git clone --depth [depth] [remote-url]
```
This operation creates so called shallow clone and can save some time cloning repos with lots of commits.

- Alternative for shallow clone is cloning just one branch. The command looks like this:


```bash
git clone [remote url] --branch [branch_name] --single-branch [folder]
```
It clones just one specified branch from our repo without other branches. It might be useful when our repo has large amount of branches and we would like to work just on one or few of them. 

- Lastly, if we have time for that, we can try cleaning up our repo. For that, the useful function might be "filter-branch". By using this command you are able to go through your history and try to indemnify big objects and trying to solve problems manually. While using such a command we rewrite the history of our project (commit ids change). Which might create additional difficulties for other developers working on this project.

2. Case with huge binary assets:

- There might be solutions for large files in repositories. But if we know that we are going to work with huge binary assets, then we should use Large File Storage (LFS).


# Git Large File Storage (LFS)

## What is Git LFS?
- [Introduction](#what-is-git-lfs)
  - Open-source Git extension designed to handle large files more efficiently in Git repositories

## Installation
- [Git Installation](#installation)
  - If you don't have Git installed, download it from: [Git Official Website](https://git-scm.com/)
- [Installing Git LFS](#installation)
  - Open Git Bash.
  - Install Git LFS by running the following command in the Git Bash:
    ```bash
    git lfs install
    ```

## Configuration
- [Initializing a Repository](#configuration)
  - Initialize a repository (or use an existing one)
- [Specifying Files to Track](#configuration)
  - Create or edit a .gitattributes file in your repository and add entries to this file for the file types you want to manage with Git LFS. For example:
    ```bash
    *.mp4 filter=lfs diff=lfs merge=lfs -text
    ```

  - Alternatively, you can specify which files should be handled by Git LFS by using the git lfs track command:
    ```bash
    git lfs track "*.mp4"
    ```

  - Do not forget to stage and commit any changes to the .gitattributes file:
    ```bash
    git add .gitattributes
    git commit -m "Track .mp4 files by Git LFS"
    ```

- [Folder Tracking](#configuration)
  - To track the whole folder you can use the following command: 
    ```bash
    git lfs track "foldername/*"
    ```

  - After running this command, you should see the following in the .gitattributes file:
    ```bash
    foldername/* filter=lfs diff=lfs merge=lfs -text
    ```
  - Stage and commit: 
    ```bash
    git add .gitattributes
    git commit -m "Track files in foldername by Git LFS"
    ```

- [Remote Repository](#configuration)
  - If you are using a remote repository, make sure it has Git LFS support to properly manage large files.
  - Also do not forget to push the changes of the .gitattributes file to the remote rpository:
    ```bash
    git push
    ```

## Usage

- After a successful configuration, you can track and commit files as usual.
- Whenever you add or commit large files with extensions specified in .gitattributes, Git will automatically use Git LFS to manage them.

## Benefits
- [Reduced Repository Size](#benefits)
  - Git LFS reduces the size of Git repositories by storing the large files externally.
- [Faster Cloning and Fetching](#benefits)
  - Smaller repositories allow for quicker cloning and fetching of code and assets.
- [Easy Configuration](#benefits)
  - Configuring Git LFS is fast and easy using a .gitattributes file
- [Seamless Integration](#benefits)
  - Git LFS integrates well with most common Git hosting services like GitHub.

## Practical Example
- [Example Usage Scenario](#practical-example)

    ```bash
    git lfs install

    git lfs track "*.jpg"

    git add large_file.jpg

    git commit -m "Add a large image file"

    git push origin main

    ```
    
## Troubleshooting
- [Troubleshooting Guide](#troubleshooting)
  - Ensure that Git LFS is installed and configured on your system by running:
    ```bash
    git lfs version
    ```
  - Check that the .gitattributes file correctly specifies which files should be tracked by Git LFS.
  - Make sure the specific file exceeds the LFS threshold for tracking (usually 100 MB).
  - If you're having authentication problems, check if you have access to the Git LFS server.
  - Ensure that the Git LFS server you're using is operational.
  - Ensure that you're using the latest version of Git LFS. Update it if not.
  - If all else fails, you can clean up your repository and re-clone it.
  - Check Git error logs for specific error messages that can help resolve the problem.

## Conclusion
- To sum up, Git Large File Storage (LFS) is an effective solution for handling large files in Git repositories. When dealing with repositories that have long commit histories or repositories with large binary assets, Git LFS makes the tracking of these files more efficient. It reduces repository size, accelerates cloning and fetching, and integrates well with Git hosting services. By using Git LFS, developers can maintain the efficiency of their version control workflow, which ensures a more productive collaboration.

## Resources
- [Git LFS GitHub Repository](#resources)
  - Link to the GitHub repository of Git LFS: [GitHub Repository](https://github.com/git-lfs/git-lfs)
- [Official Website](#resources)
  - Official Website: [Git LFS](https://git-lfs.com/)
- [Git LFS x GitHub](#resources)
  - Git LFS x GitHub: [GitHub Documentation](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage)
- [Other Sources](#resources)
  - [Atlassian Git LFS Tutorial](https://www.atlassian.com/git/tutorials/git-lfs)
  - [Smaller Repository Size](https://jasonzurita.com/smaller-repo-size-using-git-lfs/)
- [GitHub Markdown](#resources)
  - [GitHub Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Picture](#resources)
  - https://jasonzurita.com/smaller-repo-size-using-git-lfs/