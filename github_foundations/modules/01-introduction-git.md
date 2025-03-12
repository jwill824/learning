# Introduction to Git

## Module Reference

- [What is Git?](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
- [Exercise](https://learn.microsoft.com/en-us/training/modules/intro-to-git/2-exercise-configure-git)

## Study Guide Coverage

[Domain 1: Introduction to Git and GitHub](https://github.com/LadyKerr/github-certification-guide/blob/main/study-guides/gh-foundations.md#domain-1-introduction-to-git-and-github)

- [x] Describe version control
- [x] Define distributed version control
- [x] Describe Git
- [x] Explain the difference between Git and GitHub
- [x] Describe a GitHub repository
- [x] Describe a commit
- [x] Describe branching
- [x] Define a remote in Git terminology

## Key Terminology

- Version Control System (VCS): Software that tracks changes to files over time
- Repository: Storage location for a project's files and history
- Commit: Snapshot of changes at a specific point in time
- Branch: Independent line of development
- Remote: Connection to another copy of the repository
- Working Tree: Current project files you're working on
- Staging Area: Preparation area for changes before committing

## Core Concepts

> See also: [GitHub Platform Overview](./02-introduction-github.md)

1. Version Control (VCS/SCM)
   - Definition: System that tracks changes to files over time
   - Key capabilities:
     • History tracking and retrieval
     • Collaboration through [GitHub](./02-introduction-github.md)
     • Change documentation
     • [Branch management](./02-introduction-github.md#github-flow)
   - Types:
     • Centralized (older systems like SVN)
     • Distributed (Git) with [enterprise support](./03-github-products.md#enterprise-accounts)

2. Git Architecture
   - Distributed system design
   - Local repository structure:
     • Working tree (project files)
     • Staging area (changes to be committed)
     • Repository (.git directory) with [security features](./04-code-scanning.md)
   - Complete history on every clone

3. Git Objects
   - Blobs: File contents
   - Trees: Directory structures
   - Commits: Change snapshots
   - Tags: Named references
   - All identified by SHA-1 hashes

## Technical Implementation

```bash
# Initialize repository
git init -b main

# Basic workflow commands
git status                   # Check current state
git add <file>               # Stage changes
git commit -m "message"      # Record changes
git branch <name>            # Create branch
git checkout <branch>        # Switch branches
git remote add origin <url>  # Add remote
```

## Study Questions

1. Q: What is the difference between Git and GitHub?
   A: Git is a distributed version control system for tracking changes,
      while GitHub is a cloud platform that hosts Git repositories and
      adds collaboration features.

2. Q: What is a distributed version control system?
   A: A system where each user has a complete copy of the repository,
      including full history, allowing work without constant server
      connection.

## Practice Exercises

1. Repository Setup

   ```bash
   mkdir project
   cd project
   git init -b main
   git status
   ```

   - Creates new repository
   - Initializes with main branch
   - Verifies setup

2. First Commit Flow

   ```bash
   echo "# Project Title" > README.md
   git add README.md
   git commit -m "Initial commit"
   git log
   ```

   - Creates basic README
   - Demonstrates basic workflow
   - Shows history tracking

## Exam Tips

- Understand distributed vs centralized VCS
- Know the three states of Git files:
  • Modified
  • Staged
  • Committed
- Remember basic Git terminology:
  • Repository
  • Branch
  • Commit
  • Remote
- Focus on Git vs GitHub distinctions
- Know essential command purposes

## Additional Resources

- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Skills: Introduction to Git](https://skills.github.com/)
- [Git Command Explorer](https://git.gaozih.com/)
- [Interactive Git Learning](https://learngitbranching.js.org/)
