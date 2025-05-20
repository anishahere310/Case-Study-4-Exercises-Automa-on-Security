

A demonstration project showcasing GitHub's automation and security features including CI/CD workflows, CodeQL analysis, and Dependabot integration.

## Features

- **Continuous Integration**: Automated testing on every push and pull request
- **CodeQL Analysis**: Code scanning to identify security vulnerabilities
- **Dependabot Alerts**: Automated dependency updates and security notifications
- **Release Automation**: Automatic version tagging based on package.json changes

## Project Structure

```
├── .github/
│   ├── dependabot.yml         # Dependabot configuration
│   └── workflows/
│       ├── ci.yml             # CI workflow configuration
│       ├── codeql-analysis.yml # Security scanning config
│       └── release.yml        # Release automation
├── src/
│   ├── components/            # React components
│   ├── App.tsx               # Main application component
│   ├── index.css             # Global styles
│   ├── main.tsx              # Application entry point
│   └── setupTests.ts         # Test configuration
├── index.html                # HTML entry point
├── package.json              # Project dependencies
├── tailwind.config.js        # Tailwind CSS configuration
└── vitest.config.ts          # Vitest configuration
```

## Getting Started

### Prerequisites

- Node.js 16.x or higher
- npm 7.x or higher

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/yourusername/github-automation-security.git
   cd github-automation-security
   ```

2. Install dependencies
   ```bash
   npm install
   ```

3. Start the development server
   ```bash
   npm run dev
   ```

## CI/CD Workflow

Our continuous integration workflow automatically runs on every push and pull request to ensure code quality:

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
          cache: 'npm'
      - run: npm ci
      - run: npm test
```

## Security Features

### CodeQL Analysis

We use GitHub's CodeQL to scan our codebase for security vulnerabilities. The configuration can be found in `.github/workflows/codeql-analysis.yml`.

### Dependabot Alerts

Dependabot is configured to monitor our dependencies for vulnerabilities and create pull requests with updates when needed. Configuration is in `.github/dependabot.yml`.

## Release Process

When making changes that warrant a new release:

1. Update the version in `package.json`
2. Include "version bump" in your commit message
3. Push to the `main` branch
4. The release workflow will automatically create a new tag based on the version


