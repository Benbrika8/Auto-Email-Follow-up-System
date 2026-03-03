# Contributing to Auto Email Follow-up System

Thank you for your interest in contributing! This document provides guidelines for contributing to this N8N workflow project.

## Getting Started

### Prerequisites

- N8N instance (version 1.0+)
- Node.js 16+ (for local testing)
- Git for version control
- Basic understanding of N8N workflow automation

### Setting Up Development Environment

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR-USERNAME/auto-email-followup.git`
3. Install N8N locally: `npm install n8n -g`
4. Import the workflow JSON into your N8N instance
5. Configure credentials for testing

## How to Contribute

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates.

**When reporting bugs, include:**

- Clear, descriptive title
- Steps to reproduce the issue
- Expected behavior vs actual behavior
- N8N version and environment (cloud/self-hosted)
- Screenshots or execution logs if applicable
- Workflow JSON export (with credentials removed)

**Bug Report Template:**

```
**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce:
1. Configure workflow with '...'
2. Execute with data '...'
3. See error

**Expected behavior**
What you expected to happen.

**Environment:**
- N8N Version: [e.g., 1.0.5]
- Node.js Version: [e.g., 18.16.0]
- OS: [e.g., Ubuntu 22.04]
- Deployment: [Cloud/Self-hosted]

**Additional context**
Add any other context about the problem.
```

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues.

**When suggesting enhancements, include:**

- Clear, descriptive title
- Detailed description of proposed functionality
- Use case and business value
- Example workflow implementation (if possible)
- Any alternative solutions considered

### Pull Requests

**Before submitting a pull request:**

1. Create an issue describing the problem or enhancement
2. Fork the repository and create a feature branch
3. Make your changes with clear, descriptive commits
4. Test thoroughly in N8N environment
5. Update documentation (README.md) to reflect changes
6. Ensure workflow JSON is properly formatted
7. Remove all credentials and sensitive data

**Pull Request Process:**

1. Update README.md with details of changes
2. Update CHANGELOG.md with version and changes
3. Ensure workflow executes successfully
4. PR title should clearly describe the change
5. Link to related issue in PR description
6. Wait for maintainer review and address feedback

**Pull Request Template:**

```markdown
## Description
Brief description of what this PR does.

## Related Issue
Fixes #(issue number)

## Changes Made
- List specific changes
- Include new nodes added
- Document configuration changes

## Testing
Describe how you tested these changes:
- [ ] Tested in N8N cloud
- [ ] Tested in self-hosted N8N
- [ ] Tested with sample data
- [ ] All execution paths verified

## Checklist
- [ ] Code follows project style
- [ ] Documentation updated
- [ ] Credentials removed from JSON
- [ ] CHANGELOG.md updated
- [ ] Workflow executes without errors
```

## Coding Standards

### Workflow Design

- **Node Naming**: Use clear, descriptive names (e.g., "Fetch Customer Emails" not "Gmail1")
- **Comments**: Add notes to complex nodes explaining logic
- **Error Handling**: Include error trigger nodes for production workflows
- **Credentials**: Never commit credential data in JSON exports
- **Modularity**: Break complex workflows into sub-workflows when possible

### Code Nodes (JavaScript/Python)

- Follow standard language conventions (ESLint for JS)
- Add comments explaining complex logic
- Use meaningful variable names
- Handle errors gracefully with try-catch blocks
- Validate input data before processing

### Documentation

- Update README.md for any workflow changes
- Include setup instructions for new integrations
- Document required credentials and permissions
- Provide example data formats and outputs
- Add troubleshooting guides for common issues

## Workflow Testing

Before submitting changes, test:

1. **Happy Path** - Workflow executes successfully with valid data
2. **Error Cases** - Handles missing data, API failures, timeouts
3. **Edge Cases** - Empty inputs, maximum limits, special characters
4. **Credentials** - Works with fresh credential configuration
5. **Performance** - Executes within reasonable timeframe

## Commit Message Guidelines

Use clear, descriptive commit messages:

**Format:**
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature or enhancement
- `fix`: Bug fix
- `docs`: Documentation changes
- `refactor`: Code refactoring without feature changes
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(email): add spam filtering to Gmail fetch node

Added spam detection logic before email classification
to prevent auto-responding to junk mail.

Closes #42
```

```
fix(classifier): correct keyword matching for complaints

Fixed case sensitivity issue causing missed complaint
keywords. All keywords now normalized to lowercase.
```

## Code Review Process

All submissions require review:

1. Maintainer reviews code and workflow logic
2. Feedback provided via PR comments
3. Author addresses feedback and updates PR
4. Once approved, maintainer merges PR
5. Changes appear in next release

**Review Criteria:**
- Functionality works as described
- Code is clean and well-documented
- No credentials or sensitive data included
- Documentation updated appropriately
- Workflow follows project conventions

## Community Guidelines

### Code of Conduct

Be respectful and constructive:

- Use welcoming and inclusive language
- Respect differing viewpoints and experiences
- Accept constructive criticism gracefully
- Focus on what's best for the community
- Show empathy towards other contributors

### Communication Channels

- **GitHub Issues** - Bug reports and feature requests
- **Pull Requests** - Code contributions and discussions
- **Discussions** - General questions and community support

## Recognition

Contributors are recognized in:

- CHANGELOG.md for each release
- README.md contributors section
- GitHub contributor statistics

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

## Questions?

If you have questions about contributing:

- Check existing documentation and issues
- Open a GitHub Discussion for general questions
- Contact the maintainer through GitHub

---

**Thank you for contributing to open-source N8N workflow automation!**

Maintained by [Salah Eddine Benbrika](https://github.com/Benbrika8)