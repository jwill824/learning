# GitHub Products and Accounts

## Module Reference

- [GitHub Accounts and Plans](https://learn.microsoft.com/en-us/training/modules/github-accounts-plans)

## Study Guide Coverage

[Domain 1: Introduction to Git and GitHub](https://github.com/LadyKerr/github-certification-guide/blob/main/study-guides/gh-foundations.md#domain-1-introduction-to-git-and-github)

- [x] Describe the different GitHub accounts
- [x] Describe GitHub's products for personal accounts
- [x] Describe GitHub's products for organization accounts
- [x] Describe the different deployment options for GitHub Enterprise

Domain 7: Benefits of the GitHub Community

- [x] Explain how to manage organization settings
- [x] Describe members, teams, and roles in a GitHub organization

## Key Terminology

- Personal Account: Individual user identity on GitHub
- Organization: Shared account for team collaboration
- Enterprise Account: Centralized management of multiple organizations
- Plan: Subscription level determining feature access
- Billing: Payment structure for GitHub services

## Core Concepts

### 1. Account Types

Each account type provides different features and capabilities:

#### Personal Accounts

- Individual identity (username/profile)
- Resource ownership
  • [Repositories](./02-introduction-github.md#repositories)
  • Packages
  • [Projects](./07-github-projects.md)
- Action attribution
- Plans available:
  • GitHub Free
  • GitHub Pro with [Copilot](./05-github-copilot.md) integration

#### Organization Accounts

- Team collaboration focus
- Tiered permissions
- Resource sharing
- Member management
- Plans available:
  • Free for Organizations
  • GitHub Team with [Advanced Security](./04-code-scanning.md) features

#### Enterprise Accounts

- Multi-org management
- Policy enforcement
- Options:
  • Enterprise Cloud with [Codespaces](./06-github-codespaces.md)
  • Enterprise Server

### 2. Plan Features Matrix

| Feature                | Free  | Pro   | Team  | Enterprise |
|-----------------------|-------|-------|-------|------------|
| Public repos          | ∞     | ∞     | ∞     | ∞          |
| Private repos         | ∞     | ∞     | ∞     | ∞          |
| Collaborators         | ∞     | ∞     | ∞     | ∞          |
| Actions minutes/month | 2,000 | 3,000 | 3,000 | 50,000     |
| Packages storage      | 500MB | 2GB   | 2GB   | 50GB       |
| Support level         | Com.  | Email | Email | Enterprise |

### 3. Access Methods

Using [GitHub Flow](./02-introduction-github.md#github-flow) across all platforms:

#### Desktop Application

- Repository management
- Visual commit creation
- Branch management
- File comparison tools

#### Mobile Application

- Notification management
- Issue/PR collaboration
- Push notifications
- 2FA support

#### GitHub.com

- Primary web interface
- Full feature access
- Browser-based coding

## Practice Exercises

1. Account Setup

    ```bash
    # 1. Create personal account
    # 2. Enable 2FA
    # 3. Configure profile
    # 4. Set up notifications
    ```

2. Organization Management

    ```bash
    # 1. Create organization
    # 2. Configure teams
    # 3. Set permissions
    # 4. Add members
    ```

## Study Questions

1. **Q: What's the key difference between Enterprise Cloud and Server?**
   A: Enterprise Server is self-hosted with full infrastructure control,
      while Enterprise Cloud is hosted by GitHub with increased Actions
      minutes and Packages storage.

2. **Q: How do personal and organization accounts differ in permissions?**
   A: Personal accounts have direct permissions, while organization
      accounts use tiered permissions with role-based access control.

## Additional Resources

- [GitHub Pricing](https://github.com/pricing)
- [Enterprise Documentation](https://docs.github.com/enterprise-cloud)
- [Organization Management Guide](https://docs.github.com/organizations)
