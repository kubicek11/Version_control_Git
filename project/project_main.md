# Git Large File Storage (LFS)

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

### Practical Examples

### Troubleshooting

### Conclusion


### Resources:
+ Link to the GitHub repository of Git LFS: https://github.com/git-lfs/git-lfs
+ Official Website: https://git-lfs.com/
+ Git LFS x GitHub: https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage

+ Other sources:
https://www.atlassian.com/git/tutorials/git-lfs

+ GitHub Markdown: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
