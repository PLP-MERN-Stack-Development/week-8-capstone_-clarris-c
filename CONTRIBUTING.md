# Contributing to SmartFarm Management System

First off, thanks for taking the time to contribute! 🎉

The following is a set of guidelines for contributing to SmartFarm Management System. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Process](#development-process)
- [Style Guidelines](#style-guidelines)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)

## 🤝 Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

## 🚀 Getting Started

### Development Setup

1. Fork the repository on GitHub
2. Clone your fork locally
3. Set up the development environment following the [README](README.md#quick-start)
4. Create a branch for your feature or bug fix
5. Make your changes
6. Test your changes
7. Submit a pull request

### Development Environment

- Node.js 18+
- MongoDB 5.0+
- Git
- Code editor (VS Code recommended)

## 🛠️ How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check [existing issues](https://github.com/yourusername/smartfarm-management/issues) to avoid duplicates.

**Good Bug Reports Include:**
- Clear, descriptive title
- Steps to reproduce the behavior
- Expected vs actual behavior
- Screenshots (if applicable)
- Environment details (OS, browser, etc.)

**Bug Report Template:**
```markdown
**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected behavior**
What you expected to happen.

**Screenshots**
Add screenshots if applicable.

**Environment:**
- OS: [e.g. Windows 10, macOS]
- Browser: [e.g. Chrome, Safari]
- Version: [e.g. 22]
```

### Suggesting Enhancements

Enhancement suggestions are welcome! Please provide:
- Clear, descriptive title
- Detailed description of the proposed feature
- Use cases and benefits
- Any relevant mockups or examples

### Your First Code Contribution

Unsure where to start? Look for issues labeled:
- `good first issue` - easier issues for newcomers
- `help wanted` - issues where we need help
- `bug` - confirmed bugs that need fixing

## 🔄 Development Process

### Branching Strategy

We use **Git Flow** branching model:

- `main` - Production-ready code
- `develop` - Integration branch for features
- `feature/*` - Feature branches
- `hotfix/*` - Critical bug fixes
- `release/*` - Release preparation

### Branch Naming Convention

```
feature/feature-name        # New features
bugfix/bug-description     # Bug fixes
hotfix/critical-fix        # Critical fixes
docs/documentation-update  # Documentation
refactor/component-name    # Code refactoring
test/test-description      # Test additions/updates
```

### Workflow

1. **Create a branch** from `develop`
   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**
   - Write clean, readable code
   - Follow coding standards
   - Add tests for new features
   - Update documentation

3. **Test your changes**
   ```bash
   # Backend tests
   cd backend && npm test
   
   # Frontend tests
   cd frontend && npm test
   
   # E2E tests
   npm run test:e2e
   ```

4. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add crop disease detection feature"
   ```

5. **Push and create PR**
   ```bash
   git push origin feature/your-feature-name
   ```

## 📝 Style Guidelines

### JavaScript/TypeScript

We use **ESLint** and **Prettier** for code formatting:

```bash
# Install dependencies
npm install

# Check linting
npm run lint

# Fix auto-fixable issues
npm run lint:fix

# Format code
npm run format
```

**Key Style Rules:**
- Use TypeScript for new code
- Prefer `const` over `let`, avoid `var`
- Use arrow functions for callbacks
- Use meaningful variable names
- Add JSDoc comments for functions
- Keep functions small and focused

### React Components

```typescript
// ✅ Good
interface CropCardProps {
  crop: Crop;
  onUpdate: (crop: Crop) => void;
}

const CropCard: React.FC<CropCardProps> = ({ crop, onUpdate }) => {
  const handleEdit = useCallback(() => {
    onUpdate(crop);
  }, [crop, onUpdate]);

  return (
    <Card>
      <CardContent>
        <Typography variant="h6">{crop.name}</Typography>
        <Button onClick={handleEdit}>Edit</Button>
      </CardContent>
    </Card>
  );
};

export default CropCard;
```

### CSS/Styling

- Use Material-UI theme system
- Follow mobile-first responsive design
- Use semantic class names
- Avoid inline styles when possible

### API Design

```javascript
// ✅ Good API endpoint
router.get('/farms/:id/crops', authMiddleware, async (req, res) => {
  try {
    const { id } = req.params;
    const { page = 1, limit = 10 } = req.query;
    
    const crops = await Crop.find({ farm: id })
      .limit(limit * 1)
      .skip((page - 1) * limit)
      .populate('treatments');
    
    res.json({
      success: true,
      data: crops,
      pagination: { page, limit, total: crops.length }
    });
  } catch (error) {
    res.status(500).json({
      success: false,
      message: 'Failed to fetch crops',
      error: process.env.NODE_ENV === 'development' ? error.message : undefined
    });
  }
});
```

## 📝 Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/) specification:

### Format
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, etc.)
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `chore` - Maintenance tasks

### Examples
```bash
feat(auth): add OAuth2 login support
fix(crops): resolve harvest date calculation bug
docs(api): update authentication endpoints
test(farms): add integration tests for farm CRUD
refactor(dashboard): optimize query performance
```

## 🔍 Pull Request Process

### Before Creating a PR

- [ ] Your branch is up to date with `develop`
- [ ] All tests pass
- [ ] Code follows style guidelines
- [ ] Documentation is updated
- [ ] No console.log statements left in production code

### PR Template

```markdown
## Description
Brief description of changes made.

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

## How Has This Been Tested?
- [ ] Unit tests
- [ ] Integration tests
- [ ] Manual testing

## Screenshots (if applicable)
Add screenshots of UI changes.

## Checklist
- [ ] My code follows the style guidelines
- [ ] I have performed a self-review
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing unit tests pass locally with my changes
```

### Review Process

1. **Automated Checks**
   - CI/CD pipeline runs tests
   - Code quality checks
   - Security scans

2. **Code Review**
   - At least one reviewer approval required
   - Address all review comments
   - Maintain clean commit history

3. **Merge**
   - Squash and merge preferred
   - Delete feature branch after merge

## 🏷️ Labeling Issues and PRs

| Label | Description |
|-------|-------------|
| `bug` | Something isn't working |
| `enhancement` | New feature or request |
| `documentation` | Improvements or additions to docs |
| `good first issue` | Good for newcomers |
| `help wanted` | Extra attention is needed |
| `question` | Further information is requested |
| `wontfix` | This will not be worked on |

## 🚨 Security Issues

**DO NOT** open a public issue for security vulnerabilities. Instead, email us at security@smartfarm.com with:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

## 📞 Getting Help

- 💬 **Discord**: [Join our community](https://discord.gg/smartfarm)
- 📧 **Email**: developers@smartfarm.com
- 📖 **Documentation**: [Project Wiki](https://github.com/yourusername/smartfarm-management/wiki)

## 🙏 Recognition

Contributors will be recognized in:
- README.md acknowledgments
- Release notes
- Hall of Fame page (coming soon!)

---

**Thank you for contributing to SmartFarm Management System!** 🌱

Your contributions help farmers worldwide make better decisions and improve agricultural sustainability.
