

# Guide for Data Science Projects

## A Python approach

---

## Motivation

  - Data science is an iterative process
  - Data science must be reproducible
  - Data science is a teamwork matter 

---

## Agenda

  - Project structure
  - Documenting your projects
  - Git for Data Scientist
  - Helpful tools

---

## Project structure

  - Standard folders: docs, tests (if more than one file)
  - Folders for data science: data, output, models, source
  - Modules: (if more than one file) Including their Functions

---

## Some important (standard) files

setup.py: Package and distribution management
  - It should be in the folder of the source code
requirements.txt: list of dependencies
  - It helps to create virtual environments
Makefile: generic tasks
  - To use **make** Programming building utility
  
---

## Cookiecuttier

"A command-line utility that creates projects from cookiecutters (templates)"
[GitHub](https://github.com/audreyr/cookiecutter)

[Templates for data science](https://github.com/audreyr/cookiecutter#data-science)

Just execute this line to create a new project.

```bash
cookiecutter https://github.com/drivendata/cookiecutter-data-science
```

---

## References

  - [The Hitchhiker’s Guide to Python!](http://docs.python-guide.org)
  - [Cookiecutter: Better Project Templates](https://cookiecutter.readthedocs.io)

---

## Documenting your projects

---

## Basic files

### Required

README: At the root directory should give general information 
  - Purpose of the project
  - URL of the main source
  - How to install

LICENSE: specify the license under which the software is made available to the public.

### Optional 

They can be sections in README

TODO: list the planned development
CHANGELOG: changes in the code base for the latest versions

Source: [Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/writing/documentation/)

---

## Markdown

* Designed "as a format for writing for the web" (John Gruber) 
* Very easy to use (This slides are a proof!)
* Critics:
  - Many Flavors
  - Lack of semantic
[Why You Shouldn’t Use "Markdown"](http://ericholscher.com/blog/2016/mar/15/dont-use-markdown-for-technical-docs/)

Solution:
[CommonMark](http://commonmark.org)

---

## reStructuredText

* Designed for documentation
* Has semantic and roles

[Quick reStructuredText user reference](http://docutils.sourceforge.net/docs/user/rst/quickref.html)

* Comparison
[RST vs. MD](http://www.zverovich.net/2016/06/16/rst-vs-markdown.html)

---

## Libraries for documentation

Not an extensive list, just some widely used!

### [Sphinx](http://www.sphinx-doc.org)
  - It uses reStructuredText
  - Common library that uses it: [scikit-learn](https://github.com/scikit-learn/scikit-learn)

### [MKdocs](http://www.mkdocs.org/) 
  - It uses Markdown
  - Common library that uses it: [keras](https://github.com/keras-team/keras)

---

# Git for Data Scientist

---
# Version Control System

  - To work in teams smoothly
  - To keep track of history
  - DS is (sometimes) a trial & error process 

---

## Hosting services

|           | Private repositories |                  Size limits                 |                      Key advantages                     |
|-----------|----------------------|:--------------------------------------------:|:-------------------------------------------------------:|
| GitHub    |                      |         100 MB file, repository 1 GB         | Best for open source projects and build your portfolio  |
| GitLab    |           X          |               Repository 10 GB               |       Open source, it has a self-hosted free plan       |
| Bitbucket |           X          | Repository Soft limit 1 GB,  Hard limit 2 GB |        Good if using Atlassian, semantic search         |

---

## Installing

For Ubuntu, just like that!
```bash
apt-get install git
```

Or download [here!](https://git-scm.com/downloads)

First steps

```bash
git config user.name
git config user.mail
git config --global --list
```
---

## New repos


```bash
git init project_name			# Create a new project
git remote add origin url_git	# Connect repo with remote 
git remote remove origin		# Disconnect repo from remote 
git remote -v					# Check if repository is connnected
```

---
## Git Workflow

![staging-area](https://git-scm.com/images/about/index1@2x.png)

```bash
git add									# Add files to the staging-area (index)
git commit -m "describe your commit"	# Commit the files added in the staging-area
git commit -a							# Commit + add (from working directory to repo)
```
Source: <https://git-scm.com/about/staging-area>

---

## Check where we are

```bash
git status				# Show changed files and files to be committed
git log					# See history of changes
git diff id_commit		# Difference betwenn id_commit and HEAD (last commit)
git show id_commit		# See details about a commit
git gitk				# Show a graphical representation of the history
```

---

## Pull/Push

```bash
git push origin master	# Update changes in remove
git pull origin master	# Fetch and integrate from another repo or branch
```
---

## Reverting changes

```bash
git reset --hard id_commit	# Reset working directory, staging-area from id_commit
git revert -id_commit		# Reverse to id_commit
git commit -a --amend		# Amend previous commit
```
---
## Working with branches

```bash
git branch						# See branches
git branch branch_name			# Create a new branch
git checkout -b branch_name		# Create a new branch and switch to it
git checkout id_commit			# Go to the status of a commit
git checkout branch_name		# Go to the last commit
git branch --merged				# See branches merged with current
git branch -D branch_name		# Remove branch
```
---

## Collaboration

1. Clone/Fork > Pull request > 2. Review changes > 3. Pull or Merge

---
### Cloning/Forking

- Fork in hosting server then clone

```bash
git clone repo_dir			# Create a new repo with a clone of repo in repo_dir (url or folder)
```
Work and when you have something valuable request to pull your changes

---
### Pull request

```bash
git request-pull id_commit repo_dir master # Request to pull from id_commit in your master to the original repo
```
---
### Review changes

If you get a pull request (ideally) you should see what it contains

```bash
git fetch cloned_repo_dir master		# Fetch changes from the cloned repo
git log -p HEAD..FETCH_HEAD				# Review changes that are in 'FETCH_HEAD'
```

---

### Pull or Merge

For forks or branches

```bash
git pull cloned_repo_dir			# Pull changes from the cloned repo to the current
```
Or for branches

```bash
git merge branch_name				# Merge the changes from the given branch into current repo
```

---

## Useful tips

```bash
git show :/query			# Show objects that match the query
git grep -e pattern			# Look for patterns in the current branch
```
---


## Recommended readings

- [Pro Git book, written by Scott Chacon and Ben Straub ](https://git-scm.com/book/en/v2)
- [To manage big files](http://git-annex.branchable.com/)

---

# Other helpful tools

---

## Slides

### [GitPitch](https://gitpitch.com/): Markdown files
1. Create Markdown PITCHME.md
2. Push to a public repo
3. http://gitpitch.com/your_account/your_repo

### [nbpresent](https://github.com/Anaconda-Platform/nbpresent): In Jupyter notebooks

1. Install and activate

```bash
pip install nbpresent
jupyter nbextension install nbpresent --overwrite --symlink --sys-prefix
jupyter nbextension enable nbpresent --sys-prefix
jupyter serverextension enable nbpresent --sys-prefix
```

2. Edit cell types (skip, slide, sub-slide) and select a theme

---

## Dashboards

### [Jupyter dashboards](https://github.com/jupyter/dashboards)

Complement of Jupyter to arrange plots and text in a Dashboard layout.

```bash
pip install jupyter_dashboards
jupyter dashboards quick-setup --sys-prefix
```

---

## Docker Containers

### [repo2docker](https://github.com/jupyter/repo2docker)

Creates docker containers from your repo base on a [configuration file](http://repo2docker.readthedocs.io/en/latest/usage.html). 

```bash
pip install jupyter-repo2docker
jupyter-repo2docker https://github.com/your_account/your_repo
```
