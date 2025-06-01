# Git & GitHub Learning Checklist
*Complete action items based on roadmap.sh guide*

## 📚 Learn the Basics

### Understanding Version Control
- [ ] Read about what Version Control is and why it's important
- [ ] Understand why we use Version Control in software development
- [ ] Learn the differences between Git vs Other VCS (SVN, Mercurial, etc.)
- [ ] Complete a "Version Control 101" tutorial or article

### Installation and Setup
- [ ] Install Git locally on your operating system
- [ ] Verify Git installation with `git --version`
- [ ] Set up global Git configuration with your name: `git config --global user.name "Your Name"`
- [ ] Set up global Git configuration with your email: `git config --global user.email "your@email.com"`
- [ ] Understand the difference between Local vs Global Config
- [ ] Check your Git configuration with `git config --list`

### Repository Basics
- [ ] Learn what a Repository is conceptually
- [ ] Create your first repository with `git init`
- [ ] Practice Repository Initialization in different folders
- [ ] Understand the `.git` folder structure

### Core Git Commands
- [ ] Learn about the Working Directory concept
- [ ] Understand the Staging Area and its purpose
- [ ] Practice adding files to staging with `git add`
- [ ] Make your first commit with `git commit -m "message"`
- [ ] Practice Committing Changes with descriptive messages
- [ ] Create and configure a `.gitignore` file
- [ ] View commit history with `git log`
- [ ] Use `git status` to check repository state
- [ ] Practice viewing differences with `git diff`

### Branching Basics
- [ ] Understand what branches are and why they're useful
- [ ] Create your first branch with `git branch branch-name`
- [ ] Practice Creating Branches for different features
- [ ] Learn to rename branches with `git branch -m`
- [ ] Practice Renaming Branches to follow naming conventions
- [ ] Delete unnecessary branches with `git branch -d`
- [ ] Practice Deleting Branches safely
- [ ] Switch between branches with `git checkout` or `git switch`
- [ ] Practice Checkout Branch operations
- [ ] Perform your first merge with `git merge`
- [ ] Understand Merging Basics and when to use it

---

## 🐙 GitHub Essentials

### GitHub Account Setup
- [ ] Create a GitHub account
- [ ] Verify your email address
- [ ] Learn to navigate the GitHub Interface
- [ ] Set up your profile with photo and bio
- [ ] Create an impressive Profile Readme
- [ ] Add your skills, experience, and interests to profile

### Repository Management
- [ ] Create your first repository on GitHub
- [ ] Understand Private vs Public repository settings
- [ ] Practice Creating Repositories with different settings
- [ ] Learn about repository templates
- [ ] Set up repository descriptions and topics

### Git Remotes
- [ ] Understand what Git Remotes are
- [ ] Connect your local repo to GitHub with `git remote add origin`
- [ ] Practice Managing Remotes (add, remove, rename)
- [ ] Push your first changes with `git push`
- [ ] Pull changes from remote with `git pull`
- [ ] Learn Pushing/Pulling Changes workflow
- [ ] Practice Fetch without Merge using `git fetch`

### Basic Collaboration
- [ ] Understand the difference between Forking vs Cloning
- [ ] Clone your first repository with `git clone`
- [ ] Practice Cloning Repositories from different sources
- [ ] Create your first Issue on GitHub
- [ ] Learn how to use Issues for bug reports and feature requests
- [ ] Create your first Pull Request
- [ ] Practice Creating PR from your own branch
- [ ] Make a PR from a Fork to practice open source contribution
- [ ] Add Collaborators to a repository
- [ ] Accept an invitation as a collaborator

---

## 🤝 Collaboration on GitHub

### Advanced Collaboration Features
- [ ] Practice Labelling Issues and PRs for organization
- [ ] Set up Saved Replies for common responses
- [ ] Use Mentions to notify team members with @username
- [ ] Practice using Reactions for quick feedback
- [ ] Learn effective Commenting practices for code review

### Merge Strategies
- [ ] Understand Fast-Forward vs Non-FF merges
- [ ] Practice Handling Conflicts when they occur
- [ ] Learn how to Rebase branches for cleaner history
- [ ] Practice Squash merging to combine commits
- [ ] Use Cherry Picking Commits to move specific changes

### Best Practices
- [ ] Learn to write good Commit Messages
- [ ] Establish Branch Naming conventions
- [ ] Follow PR Guidelines for effective reviews
- [ ] Practice Code Reviews on others' pull requests
- [ ] Write Contribution Guidelines for your projects
- [ ] Create comprehensive Documentation
- [ ] Master Markdown syntax for GitHub
- [ ] Write an excellent Project Readme
- [ ] Set up GitHub Wikis for extended documentation
- [ ] Maintain Clean Git History

---

## 👥 Working in a Team

### GitHub Organizations
- [ ] Create or join a GitHub Organization
- [ ] Understand Collaborators vs Members roles
- [ ] Set up Teams within Organization
- [ ] Configure team permissions and access levels

### Project Management
- [ ] Set up GitHub Projects for your team
- [ ] Practice Project Planning with GitHub tools
- [ ] Create and use Kanban Boards
- [ ] Build project Roadmaps for long-term planning
- [ ] Set up Automations for project management
- [ ] Use GitHub Discussions for team communication

---

## 🔧 Intermediate Git Topics

### Git Stash and History
- [ ] Learn Git Stash Basics for temporary storage
- [ ] Practice stashing work in progress
- [ ] Understand project History and timeline
- [ ] Learn difference between Linear vs Non-Linear history
- [ ] Understand what HEAD pointer represents
- [ ] Experience and recover from Detached HEAD state
- [ ] Master various git log options for history viewing

### Undoing Changes
- [ ] Use git revert to safely undo commits
- [ ] Learn git reset with --soft option
- [ ] Practice git reset with --hard option (carefully!)
- [ ] Understand git reset with --mixed option
- [ ] Master Undoing Changes in different scenarios

### Viewing Differences
- [ ] View diffs Between Commits
- [ ] Compare differences Between Branches
- [ ] Check Staged Changes before committing
- [ ] Review Unstaged Changes in working directory

### Rewriting History
- [ ] Modify last commit with git commit --amend
- [ ] Learn interactive rebase with git rebase -i
- [ ] Practice git rebase for cleaner history
- [ ] Use git filter-branch for bulk changes (advanced)
- [ ] Understand when to use git push --force (dangerous!)

### Tags and Releases
- [ ] Create tags for version marking
- [ ] Practice Managing Tags (create, delete, list)
- [ ] Push tags to remote with Pushing Tags
- [ ] Checkout specific tags to view old versions
- [ ] Create GitHub Releases from tags

---

## 🪝 Git Hooks

### Understanding Hooks
- [ ] Learn What and Why Git hooks exist
- [ ] Understand Client vs Server Hooks
- [ ] Set up a commit-msg hook
- [ ] Create a post-checkout hook
- [ ] Implement a post-update hook
- [ ] Set up a pre-commit hook for code quality
- [ ] Create a pre-push hook for testing
- [ ] Practice with other Common Hooks

---

## 📦 Submodules

### Working with Submodules
- [ ] Understand What and Why to use Submodules
- [ ] Practice Adding Submodules to projects
- [ ] Learn Updating Submodules workflow
- [ ] Handle submodule dependencies properly

---

## 💻 GitHub Workflow

### GitHub CLI
- [ ] Complete GitHub CLI Installation and Setup
- [ ] Practice Repository management via CLI
- [ ] Use CLI for Issue Management
- [ ] Create and manage Pull Requests from command line

---

## ⚡ GitHub Actions

### Actions Basics
- [ ] Learn YAML Syntax for workflow files
- [ ] Set up basic Workflow Triggers (push, pull request)
- [ ] Create Scheduled Workflows with cron
- [ ] Understand Workflow Runners (GitHub-hosted vs self-hosted)
- [ ] Learn about Workflow Context variables
- [ ] Set up Secrets and Environment Variables
- [ ] Implement Caching Dependencies for faster builds
- [ ] Practice Storing Artifacts from workflows
- [ ] Monitor Workflow Status and add badges
- [ ] Explore Marketplace Actions for common tasks

### Advanced Actions
- [ ] Understand various Usecases for GitHub Actions
- [ ] Implement What are these? advanced workflow patterns
- [ ] Use GitHub Actions in Automation pipelines

---

## 🩹 Git Patch

### Patch Operations
- [ ] Learn to create Git Patch files
- [ ] Practice applying patches to repositories
- [ ] Use patches for code sharing and review

---

## 🚀 Advanced Git Topics

### Advanced Git Commands
- [ ] Master Git Reflog for recovery operations
- [ ] Use Git Bisect to find bugs with binary search
- [ ] Set up Git Worktree for multiple working directories
- [ ] Configure Git Attributes for repository behavior
- [ ] Implement Git LFS for large file management

---

## 🔌 GitHub API & Developer Tools

### API Integration
- [ ] Explore GitHub REST API capabilities
- [ ] Learn GitHub GraphQL API for advanced queries
- [ ] Understand Creating Apps on GitHub

### App Development
- [ ] Build a simple GitHub App
- [ ] Create an OAuth App for user authentication
- [ ] Set up Webhooks for real-time notifications

---

## 🌟 More GitHub Features

### Extended Platform Features
- [ ] Set up GitHub Sponsors (if applicable)
- [ ] Deploy a site using GitHub Pages
- [ ] Configure Deploying Static Websites
- [ ] Set up Custom Domains for GitHub Pages
- [ ] Use Static Site Generators with GitHub Pages
- [ ] Create and share GitHub Gists
- [ ] Publish packages to GitHub Packages
- [ ] Try GitHub Codespaces for cloud development

### Education and Community
- [ ] Explore GitHub Education resources
- [ ] Apply for Student Developer Pack (if student)
- [ ] Try GitHub Classroom (if educator)
- [ ] Join Campus Program (if applicable)
- [ ] Browse GitHub Marketplace for integrations

### Security and AI
- [ ] Enable GitHub Security features
- [ ] Explore GitHub Models (if available)
- [ ] Try GitHub Copilot for AI-assisted coding

---

# Resources
- [Roadmap.sh](https://roadmap.sh/git-github)