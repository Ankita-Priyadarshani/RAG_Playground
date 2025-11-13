# Contributing to RAG Playground

Thank you for your interest in contributing to the RAG Playground! We welcome bug reports and pull requests to help improve this project.

---

## Table of Contents

- [Basics](#basics)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)
- [Pull Requests](#pull-requests)
- [Development Workflow](#development-workflow)
- [Testing Your Work](#testing-your-work)
- [Write Documentation](#write-documentation)
- [Releasing a New Version](#releasing-a-new-version)

---

## Basics

1. Create an issue and describe your idea
2. Fork the repository
3. Create your feature branch (`git checkout -b my-new-feature`)
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Publish the branch (`git push origin my-new-feature`)
6. Create a new Pull Request

---

## Reporting Bugs

Before creating a bug report, please check existing issues to avoid duplicates.

When filing a bug report, include:

- **Clear title**: Describe the issue concisely
- **Steps to reproduce**: Provide detailed steps to reproduce the bug
- **Expected behavior**: What you expected to happen
- **Actual behavior**: What actually happened
- **Environment**: Browser, OS, versions of dependencies
- **Screenshots**: If applicable
- **Error messages**: Full error messages and stack traces

**Example:**
```
Title: Vector database creation fails with FAISS

Steps to reproduce:
1. Open sidebar and click "Create New Knowledge Base"
2. Enter name "test_kb"
3. Click Create

Expected: New knowledge base should be created
Actual: Upload fails with "Cannot initialize FAISS engine" error

Environment: Chrome 119, Windows 11, React 17
```

## Suggesting Enhancements

Enhancement suggestions are welcome! Please provide:

- **Clear description**: What enhancement you'd like to see
- **Use case**: Why this enhancement would be valuable
- **Proposed solution**: Your ideas on how to implement it
- **Alternatives considered**: Other approaches you've thought about

## Pull Requests

Pull requests are the best way to contribute code. Please follow these steps:

1. **Create an issue first**: Discuss your proposed changes
2. **Fork the repository**: Create your own fork
3. **Create a branch**: Use a descriptive branch name
4. **Make your changes**: Follow our coding standards
5. **Test thoroughly**: Ensure all tests pass
6. **Update documentation**: If needed
7. **Submit the PR**: With a clear description

---

## Development Workflow

### Step 1: Install Requirements

```bash
# Install frontend dependencies
cd assets/client
pnpm install

# Install Python dependencies
pip install numpy pandas openai tiktoken
```

### Step 2: Configure Environment

Create a `.env` file in the `assets/client` directory:
```env
MODULE=your-module-name
ACCESS_KEY=your-access-key
SECRET_KEY=your-secret-key
APP=your-app-id
EMBEDDER_ENGINE=your-embedding-engine-id
```

### Step 3: Run & Debug

```bash
# Start development server
cd assets/client
pnpm dev

# Application will be available at http://localhost:3000
```

### Step 4: Test It

```bash
# Lint code
pnpm lint

# Type check
pnpm type-check

# Build frontend
pnpm build
```

---

## Testing Your Work

You can test your changes by running the application locally and verifying:

- The application builds without errors
- Linting passes: `pnpm lint`
- Type checking passes: `pnpm type-check`
- The workflow functions as expected
- No regressions in existing features

```bash
# Run checks
pnpm lint
pnpm type-check
pnpm build
```

---

## Write Documentation

This project has documentation in a few places:

### README.md
The main README provides an overview, installation instructions, and usage guidelines. Update this file when adding major features or changing how the application works.

### Code Comments
Add clear comments for complex logic. Use JSDoc style for functions and components:

```typescript
/**
 * Uploads documents to vector database and creates embeddings
 * 
 * @param files - The document files to upload (PDF, DOCX, PPT, or TXT)
 * @param vectorDBId - The ID of the vector database
 * @returns Promise resolving to the upload results
 */
async function uploadDocuments(files: File[], vectorDBId: string): Promise<UploadResult[]> {
    // Implementation
}
```

---

## Releasing a New Version

1. Ensure all tests pass and the build is successful
2. Update version number in `package.json`
3. Create a Git tag: `git tag -a v0.1.0 -m "Release version 0.1.0"`
4. Push the changes: `git push`
5. Push the tag: `git push --tags`
6. Build the application:
   ```bash
   cd assets/client
   pnpm build
   ```
7. Create deployment package with required files
8. Deploy to GovConnect.ai following deployment instructions in README.md

---
