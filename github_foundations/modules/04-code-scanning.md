# Code Scanning with GitHub

## Module Reference

- [Code Scanning with GitHub](https://learn.microsoft.com/en-us/training/modules/code-scanning-github/)
- [GitHub Skills: Secure your repository](https://github.com/skills/secure-repository-supply-chain)
- [CodeQL Documentation](https://codeql.github.com/docs/)

## Study Guide Coverage

[Domain 6: Privacy, Security, and Administration](https://github.com/LadyKerr/github-certification-guide/blob/main/study-guides/gh-foundations.md#domain-6-privacy-security-and-administration)

- [x] Describe the main features and options in the Security tab
- [x] Explain how to enable and disable features

## Key Terminology

- CodeQL: GitHub's semantic code analysis engine
- SARIF: Static Analysis Results Interchange Format
- Code Scanning: Automated security vulnerability detection
- Default Setup: Quick automated configuration option
- Advanced Setup: Customizable workflow configuration

## Core Concepts

### 1. Code Scanning Fundamentals

- Purpose:
  • Find security vulnerabilities
  • Detect coding errors
  • Prevent new problems
- Availability:
  • All public repositories
  • Private repos with [GitHub Advanced Security](./03-github-products.md#enterprise-accounts)
- Analysis Types:
  • [CodeQL](https://codeql.github.com/docs/) analysis
  • Third-party tool integration
  • Custom analysis patterns

### 2. CodeQL Analysis

- Features:
  • Code-as-data analysis approach
  • Database generation of codebase
  • Query-based vulnerability detection
- Supported Languages:
  • C/C++
  • C#
  • Go
  • Java/Kotlin
  • JavaScript/TypeScript
  • Python
  • Ruby
  • Swift

### 3. Setup Options

1. Default Setup:
   - Quick configuration
   - Automated language detection
   - Standard query selection
   - GitHub Actions integration

2. Advanced Setup:
   - Custom workflow file
   - Configurable scanning options
   - Advanced query selection
   - CI/CD integration options

3. External CI Integration:
   - Custom CI system usage
   - SARIF file uploads
   - API integration options

## Technical Implementation

```yaml
# Example CodeQL workflow
name: "CodeQL"
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  schedule:
    - cron: '0 0 * * 0'

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: github/codeql-action/init@v2
      - uses: github/codeql-action/analyze@v2
```

## Practice Exercises

1. Enable Default Setup

    ```bash
    # Via GitHub UI:
    # 1. Navigate to Security > Code scanning
    # 2. Click "Set up code scanning"
    # 3. Choose "Default"
    # 4. Select languages
    # 5. Enable CodeQL
    ```

2. Review Scan Results

    ```bash
    # 1. Check Actions tab for scan completion
    # 2. Navigate to Security > Code scanning
    # 3. Review and triage alerts
    # 4. Create issues for valid findings
    ```

## Study Questions

1. **Q: What are the key differences between Default and Advanced setup?**
   A: Default setup provides automated configuration with standard
      options, while Advanced setup allows custom workflow files
      and detailed scanning configuration.

2. **Q: How does CodeQL differ from traditional static analyzers?**
   A: CodeQL treats code as queryable data, enabling semantic
      analysis and more accurate vulnerability detection with
      fewer false positives.

## Additional Resources

- [Advanced Security Documentation](https://docs.github.com/en/code-security)
- [CodeQL Query Examples](https://github.com/github/codeql)
- [SARIF Format Specification](https://sarifweb.azurewebsites.net/)
