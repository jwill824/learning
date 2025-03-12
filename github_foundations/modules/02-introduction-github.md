# Introduction to GitHub

## Module Reference

- [What is GitHub?](https://learn.microsoft.com/en-us/training/modules/introduction-to-github/)
- [Exercise](https://learn.microsoft.com/en-us/training/modules/introduction-to-github/6-guided-tour-of-github)
- [GitHub Skills: First Day on GitHub](https://github.com/skills/introduction-to-github)
- [GitHub Skills: First Week on GitHub](https://github.com/skills/first-week-on-github)

## Study Guide Coverage

[Domain 1: Introduction to Git and GitHub](https://github.com/LadyKerr/github-certification-guide/blob/main/study-guides/gh-foundations.md#domain-1-introduction-to-git-and-github)

- [x] Describe GitHub
- [x] Explain the difference between Git and GitHub
- [x] Describe a GitHub repository
- [x] Describe the GitHub flow

[Domain 3: Collaboration Features](https://github.com/LadyKerr/github-certification-guide/blob/main/study-guides/gh-foundations.md#domain-3-collaboration-features)

- [x] Describe how to create an issue
- [x] Describe the difference between an issue, discussion, and pull request
- [x] Describe a pull request
- [x] Describe how to manage notification subscriptions

## Key Terminology

- Repository: Project storage space containing files and version history
- Branch: Independent line of development
- Pull Request: Proposed changes ready for review
- Issue: Tracked unit of work (bug, feature, etc.)
- Discussion: Forum-style conversation space
- GitHub Flow: Branching-based workflow for collaboration
- Gist: Shareable code snippets
- Wiki: Project documentation space

## Core Concepts

### 1. GitHub Enterprise Platform

> See also: [GitHub Products Overview](./03-github-products.md)

- AI Integration:
  • [GitHub Copilot](./05-github-copilot.md) for development
  • AI-powered PR and issue analysis
  • Automated [security checks](./04-code-scanning.md)
- Collaboration Features:
  • Repositories with [advanced security](./04-code-scanning.md)
  • [Issues and PR system](./07-github-projects.md)
  • Team workflow tools
- Development Tools:
  • [Codespaces](./06-github-codespaces.md) for cloud development
  • [Projects](./07-github-projects.md) for work tracking
  • [Markdown](./08-markdown.md) for documentation
- Security Framework:
  • Native security features
  • Private code protection
  • Dependabot integration
- Platform Scale:
  • 100M+ developers
  • 330M+ repositories
  • Global deployment

### 2. GitHub Flow

> See also: [Pull Requests](./03-collaboration-features.md#pull-requests)

- Branch creation from [Git base](./01-introduction-git.md)
- Changes and commits
- Pull request creation
- Review process
- Merge and cleanup

```bash
# 1. Create Branch
git checkout -b feature-branch

# 2. Make Changes
git add .
git commit -m "Changes description"

# 3. Create Pull Request
# (Done via GitHub UI)

# 4. Review & Discussion
# (Happens in PR interface)

# 5. Merge
# (After approval)

# 6. Delete Branch
git branch -d feature-branch
```

### 3. Collaboration Tools

> See also: [Project Management](./05-project-management.md)

1. Issues
   - Track tasks, bugs, features
   - Creation methods:
     • Repository directly
     • Task list items
     • Project notes
     • Code references

2. Discussions
   - Categories:
     • Announcements
     • Q&A
     • Ideas
     • Show and tell
     • Polls
   - Visibility inherits from repository

3. Notifications
   - Subscription types:
     • Conversations
     • CI activity
     • Repository events
     • Security alerts

## Practice Exercises

1. Repository Creation

   ```bash
   # Via GitHub UI:
   # 1. Click '+' > New repository
   # 2. Set name and visibility
   # 3. Initialize with README
   ```

2. GitHub Flow Practice

   ```bash
   # 1. Clone repository
   git clone <repository-url>
   
   # 2. Create feature branch
   git checkout -b feature-xyz
   
   # 3. Make changes and commit
   git add .
   git commit -m "Add feature xyz"
   
   # 4. Push and create PR
   git push origin feature-xyz
   ```

## Study Questions

1. Q: What distinguishes GitHub Discussions from Issues?
   A: Discussions are for open-ended conversations and community
      engagement, while Issues track specific tasks, bugs, or features.

2. Q: What are the key components of GitHub Flow?
   A: Create branch > Make changes > Create PR > Review >
      Merge > Delete branch

## Additional Resources

- [GitHub Flow Guide](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitHub Features](https://github.com/features)
- [GitHub Guides](https://guides.github.com/)
