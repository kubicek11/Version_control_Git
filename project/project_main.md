# Git large repositories

Having large repositories creates problems that may influence the performance of our work. We can encounter these difficulties while working with remote repositories (cloning, pushing, etc.)

Besides that, platforms that provide various functionalities related to version control might have size limits for files that you want to push.

 - GitHub has file size limits that include a warning for files larger than 50 MiB and a strict prohibition against files larger than 100 MiB. Additionally, GitHub recommends that entire repositories be smaller than 1GB and strongly advises keeping repositories smaller than 5GB, although these recommendations are not strict size limits.
+ GitHub large files: https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github

### We can distinguish two types of big repositories:

1. Repositories with long history (containing a lont of commits over long periods of time)

2. Repositories which include huge binary assets (usually refers to files that contain something	 else than plain text, those can be: compressed files, videos, images, or any other non-text data).

### Solving problems with large repositories:

 1.The case with long histories:
 - Sometimes we need keep the history of our repository intact. In that case to solve complications while cloning repository we can clone just n latest commits. We can use:


```bash
git clone --depth [depth] [remote-url]
```
This operation creates so called shallow clone and can save some time cloning repos with lots of commits.

- Alternative for shallow clone is cloning just one branch. The command looks like this:


```bash
git clone [remote url] --branch [branch_name] --single-branch [folder]
```
It cleans just one specified branch from our repo without other branches. It might be useful when our repo has large amount of branches and we would like to work just on one or few of them. 


# Git Large File Storage (LFS)

![](logo.png)

### What is Git LFS?

Git extension used to manage large files.

+ Open-source Git extension designed to handle large files more efficiently in Git repositories

### Installation

1. If you don't have Git installed, download it from:
   [Git Official Website](https://git-scm.com/)

2. Open Git Bash.

3. Install Git LFS by running the following command in the Git Bash:

```bash
git lfs install
```

4. Now that the Git LFS is installed, you can use it to track large files in your repositories.

### Configuration
1. Initialize a repository (or use an existing one)

2. Specify which files to track:

Create or edit a .gitattributes file in your repository and add entries to this file for the file types you want to manage with Git LFS. For example:

```bash
*.mp4 filter=lfs diff=lfs merge=lfs -text
```

If you are using a remote repository, make sure it has Git LFS support to properly manage large files.
   
### Usage
After a successfull configuration you can track and commit files as usual.

Whenever you add or commit large files with extensions specified in .gitattributes, Git will automatically use Git LFS to manage them.

### Benefits

1. Reduced Repository Size

Git LFS reduces the size of Git repositories by storing the large files externally.

2. Faster Cloning and Fetching

Smaller repositories allow for quicker cloning and fetching of code and assets.

3. Easy Configuration

Configuring Git LFS is fast and easy using a .gitattributes file

4. Seamless Integration 

Git LFS integrates well with most common Git hosting services like GitHub.

### Practical Examples

### Troubleshooting
1. Ensure that Git LFS is installed and configured on your system by running:

```bash
git lfs version
```

3. Check that the .gitattributes file correctly specifies which files should be tracked by Git LFS. 

4. Make sure the specific file exceeds the LFS threshold for tracking (usually 100 MB). 

5. If you're having authentication problems, check if you have access to the Git LFS server.

6. Ensure that the Git LFS server you're using is operational.
   
7. Ensure that you're using the latest version of Git LFS. Update it if not.
   
8. If all else fails, you can clean up your repository and re-clone it.

9. Check Git error logs for specific error messages that can help reaolve the problem.

### Conclusion

### Resources:
+ Link to the GitHub repository of Git LFS: https://github.com/git-lfs/git-lfs
+ Official Website: https://git-lfs.com/
+ Git LFS x GitHub: https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage

+ Other sources:
https://www.atlassian.com/git/tutorials/git-lfs

https://jasonzurita.com/smaller-repo-size-using-git-lfs/

+ GitHub Markdown: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
