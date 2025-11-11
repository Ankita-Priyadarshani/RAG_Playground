# How to Contribute

Thank you for your interest in contributing to the RAG Playground! Bug reports, feature requests, and pull requests from users are what keep this project working and improving.

This document provides guidelines for contributing to the project. Please take a moment to review this document to make the contribution process smooth and effective for everyone involved.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Features](#suggesting-features)
  - [Submitting Pull Requests](#submitting-pull-requests)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Testing Requirements](#testing-requirements)
- [Documentation Guidelines](#documentation-guidelines)
- [Additional Resources](#additional-resources)

---

## Code of Conduct

This project and everyone participating in it is governed by our commitment to creating a welcoming and inclusive environment. By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

### Our Standards

- **Be respectful**: Treat all contributors with respect and courtesy
- **Be collaborative**: Work together and help each other
- **Be inclusive**: Welcome newcomers and diverse perspectives
- **Be professional**: Maintain professional conduct in all interactions
- **Be constructive**: Provide constructive feedback and be open to receiving it

---

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16 or higher)
- **pnpm** package manager
- **Python** 3.8+
- **Git** for version control
- **Access to SEMOSS platform** (for testing)

### Setting Up Your Development Environment

1. **Fork the repository** on the project's hosting platform
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/rag-playground.git
   cd rag-playground
   ```

3. **Add the upstream repository**:
   ```bash
   git remote add upstream https://github.com/original-org/rag-playground.git
   ```

4. **Install frontend dependencies**:
   ```bash
   cd assets/client
   pnpm install
   ```

5. **Install Python dependencies**:
   ```bash
   pip install numpy pandas openai tiktoken
   ```

6. **Configure environment variables**:
   - Copy `.env.example` to `.env` in `assets/client`
   - Fill in your SEMOSS credentials and configuration

7. **Start the development server**:
   ```bash
   pnpm dev
   ```

---

## How Can I Contribute?

### Reporting Bugs

Before creating a bug report, please check existing issues to avoid duplicates.

**When submitting a bug report, include:**

- **Clear, descriptive title** for the issue
- **Detailed description** of the problem
- **Steps to reproduce** the issue
- **Expected behavior** vs. actual behavior
- **Screenshots or error messages** (if applicable)
- **Environment details**:
  - OS and version
  - Node.js version
  - Browser and version
  - SEMOSS version

**Example Bug Report:**

```markdown
### Bug: Vector database creation fails with FAISS

**Description**: When creating a new vector database with FAISS type, the operation fails with error "Cannot initialize FAISS engine".

**Steps to Reproduce**:
1. Click "Create New Knowledge Base"
2. Enter name "test_kb"
3. Select FAISS as vector type
4. Click Create

**Expected**: New knowledge base should be created
**Actual**: Error message appears

**Environment**:
- OS: Windows 11
- Node.js: v18.16.0
- Browser: Chrome 118
- SEMOSS: 4.3.5

**Error Message**:
```
Error: Cannot initialize FAISS engine
at CreateVectorDatabaseEngine (line 187)
```
```

### Suggesting Features

We welcome feature suggestions! Before submitting, please:

1. **Check existing feature requests** to avoid duplicates
2. **Clearly describe the feature** and its benefits
3. **Provide use cases** for the feature
4. **Consider implementation complexity**

**Feature Request Template:**

```markdown
### Feature Request: [Feature Name]

**Problem Statement**: 
Describe the problem this feature would solve.

**Proposed Solution**:
Describe your proposed solution in detail.

**Alternative Solutions**:
Describe any alternative solutions you've considered.

**Use Cases**:
- Use case 1
- Use case 2

**Benefits**:
- Benefit 1
- Benefit 2

**Implementation Considerations**:
Any technical details or challenges to consider.
```

### Submitting Pull Requests

#### Basics

1. **Create an issue** describing your proposed changes (if one doesn't exist)
2. **Fork the repository** to your GitHub account
3. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
4. **Make your changes** following our coding standards
5. **Test your changes** thoroughly
6. **Commit your changes** with clear commit messages:
   ```bash
   git commit -m "Add: Brief description of changes"
   ```
7. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```
8. **Create a Pull Request** with a clear description

#### Pull Request Guidelines

**PR Title Format:**
- `Add: [New feature description]`
- `Fix: [Bug description]`
- `Update: [Component/feature updated]`
- `Refactor: [What was refactored]`
- `Docs: [Documentation changes]`

**PR Description Should Include:**
- Reference to related issue(s)
- Summary of changes
- Motivation and context
- Testing performed
- Screenshots (for UI changes)
- Breaking changes (if any)

**Example PR Description:**

```markdown
## Related Issue
Fixes #123

## Summary
Added ability to upload multiple files at once to knowledge base.

## Changes
- Updated VectorModal component to accept multiple files
- Modified upload handler to process files sequentially
- Added progress indicator for batch uploads
- Updated documentation

## Testing
- Tested with 5 PDF files (total 50MB)
- Tested with mixed file types (PDF, DOCX, TXT)
- Tested error handling for invalid files
- Verified embeddings created correctly

## Screenshots
[Attach screenshots]

## Breaking Changes
None
```

---

## Development Workflow

### Branch Naming Convention

- `feature/feature-name` - New features
- `fix/bug-description` - Bug fixes
- `refactor/component-name` - Code refactoring
- `docs/description` - Documentation updates
- `test/test-description` - Test additions/updates

### Commit Message Guidelines

Follow the conventional commits format:

```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, no logic change)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Example:**
```
feat: Add batch file upload to knowledge base

- Implement multi-file selection in VectorModal
- Add sequential processing for multiple files
- Include progress tracking for batch uploads

Closes #123
```

### Keeping Your Fork Updated

```bash
# Fetch upstream changes
git fetch upstream

# Merge upstream changes into your local main branch
git checkout main
git merge upstream/main

# Update your fork on GitHub
git push origin main
```

---

## Coding Standards

### TypeScript / JavaScript

- **Use TypeScript** for all new code
- **Follow ESLint rules** configured in the project
- **Use functional components** and React Hooks
- **Avoid any type** - use proper typing
- **Use meaningful variable names** - be descriptive
- **Add JSDoc comments** for complex functions
- **Keep functions small** and focused on a single task

**Example:**

```typescript
/**
 * Uploads a file to the vector database and creates embeddings
 * @param file - The file to upload
 * @param vectorDBId - ID of the target vector database
 * @returns Promise<UploadResult> - Result of the upload operation
 */
const uploadFileToVectorDB = async (
  file: File,
  vectorDBId: string
): Promise<UploadResult> => {
  // Implementation
};
```

### Python

- **Follow PEP 8** style guide
- **Use type hints** where appropriate
- **Write docstrings** for all functions and classes
- **Keep functions focused** on single responsibility
- **Use meaningful variable names**

**Example:**

```python
def order_document_sections_by_query_similarity(
    query: str, 
    contexts: dict[(str, str), np.array]
) -> list[(float, (str, str))]:
    """
    Order document sections by their similarity to the query.
    
    Args:
        query: The user's query text
        contexts: Dictionary mapping document sections to their embeddings
        
    Returns:
        List of (similarity_score, section_id) tuples, sorted by similarity
    """
    # Implementation
```

### Component Structure

```typescript
// Imports
import { useState } from 'react';
import { styled } from '@mui/material/styles';

// Types/Interfaces
interface ComponentProps {
  prop1: string;
  prop2: number;
}

// Styled Components
const StyledContainer = styled('div')(({ theme }) => ({
  padding: theme.spacing(2),
}));

// Component
export const Component: React.FC<ComponentProps> = ({ prop1, prop2 }) => {
  // State
  const [state, setState] = useState('');
  
  // Effects
  useEffect(() => {
    // Effect logic
  }, []);
  
  // Handlers
  const handleClick = () => {
    // Handler logic
  };
  
  // Render
  return (
    <StyledContainer>
      {/* JSX */}
    </StyledContainer>
  );
};
```

### CSS / Styling

- **Use Material UI's styling solution** (styled components)
- **Use theme variables** for colors, spacing, etc.
- **Make components responsive**
- **Follow accessibility guidelines**

---

## Testing Requirements

### Running Tests

```bash
# Run all tests
pnpm test

# Run tests in watch mode
pnpm test:watch

# Run tests with coverage
pnpm test:coverage
```

### Testing Checklist

Before submitting a PR, ensure:

- [ ] All existing tests pass
- [ ] New features include tests
- [ ] Bug fixes include regression tests
- [ ] Tests cover edge cases
- [ ] Manual testing performed
- [ ] UI changes tested in multiple browsers
- [ ] Responsive design tested on different screen sizes

### Testing Guidelines

- **Write unit tests** for utility functions
- **Write integration tests** for component interactions
- **Test error handling** and edge cases
- **Mock external dependencies** (API calls, SEMOSS SDK)
- **Aim for high coverage** but prioritize meaningful tests

---

## Documentation Guidelines

### Code Documentation

- **Comment complex logic** - explain the "why", not the "what"
- **Update JSDoc/docstrings** when modifying functions
- **Keep comments up-to-date** with code changes
- **Use TODO comments** for future improvements

### README Updates

When your changes affect usage:

- Update the **Installation** section if dependencies change
- Update the **Configuration** section for new config options
- Update the **Usage** section for new features
- Add examples for new functionality

### Changelog

Document your changes in the appropriate format:

```markdown
## [Version] - YYYY-MM-DD

### Added
- New feature description

### Changed
- Modified feature description

### Fixed
- Bug fix description

### Deprecated
- Deprecated feature description

### Removed
- Removed feature description
```

---

## Additional Resources

### Project Documentation
- [README.md](README.md) - Project overview and usage
- [Architecture Documentation](docs/ARCHITECTURE.md) - System architecture
- [API Documentation](docs/API.md) - API reference

### External Resources
- [SEMOSS SDK Documentation](https://semoss.org/documentation)
- [React Documentation](https://react.dev)
- [TypeScript Documentation](https://www.typescriptlang.org/docs)
- [Material UI Documentation](https://mui.com)
- [OpenAI API Documentation](https://platform.openai.com/docs)

### Getting Help

- **Issues**: Check existing issues or create a new one
- **Discussions**: Join project discussions for questions
- **Email**: Contact project maintainers for sensitive matters

---

## Recognition

Contributors will be recognized in:
- Project README acknowledgments
- Release notes for their contributions
- GitHub contributors page

---

Thank you for contributing to RAG Playground! Your efforts help make this project better for everyone. 🎉

**Questions?** Don't hesitate to ask in the issues or discussions section.
