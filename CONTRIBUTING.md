# Contributing to Booeb.com

Thank you for your interest in contributing to Booeb.com! We appreciate your help in making this marketplace platform better.

## 🎯 Code of Conduct

We are committed to providing a welcoming and inclusive environment for all contributors.

## 🚀 Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/Booeb.com.git
   cd Booeb.com
   ```

3. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Install dependencies**:
   ```bash
   npm run install:all
   ```

5. **Start development**:
   ```bash
   npm run dev
   ```

## 📝 Development Workflow

### Branch Naming Convention

- `feature/description` - New features
- `bugfix/description` - Bug fixes
- `hotfix/description` - Urgent production fixes
- `refactor/description` - Code refactoring
- `docs/description` - Documentation updates
- `test/description` - Adding tests

### Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat:` A new feature
- `fix:` A bug fix
- `docs:` Documentation only changes
- `style:` Changes that do not affect code meaning
- `refactor:` Code refactoring without feature changes
- `perf:` Performance improvements
- `test:` Adding or updating tests
- `chore:` Build process, dependencies, tools

**Examples:**
```
feat(auth): add social login integration

fix(cart): resolve quantity update issue

docs(api): update endpoint documentation
```

## 🛠️ Code Standards

### Frontend (React/Next.js)

- Use **TypeScript** for type safety
- Follow **ESLint** configuration
- Use **Prettier** for code formatting
- Component structure:
  ```
  ComponentName/
  ├── ComponentName.tsx
  ├── ComponentName.module.css
  ├── ComponentName.test.tsx
  └── index.ts
  ```

- **Naming Conventions:**
  - Components: PascalCase (`ProductCard.tsx`)
  - Hooks: camelCase starting with `use` (`useProducts.ts`)
  - Constants: UPPER_SNAKE_CASE (`API_BASE_URL`)
  - Utilities: camelCase (`formatPrice.ts`)

### Backend (Node.js/Express)

- Use **TypeScript** for type safety
- Follow **ESLint** configuration
- Use **Prettier** for code formatting
- Structure:
  ```
  routes/
  ├── products.ts
  controllers/
  ├── productController.ts
  models/
  ├── Product.ts
  ```

- **Error Handling:**
  ```typescript
  catch (error) {
    logger.error('Error message:', error);
    res.status(500).json({ error: 'Internal server error' });
  }
  ```

## ✅ Testing

### Frontend Testing
```bash
npm run test:frontend
```

- Write tests for all components
- Use Jest & React Testing Library
- Aim for >80% coverage

### Backend Testing
```bash
npm run test:backend
```

- Write tests for all API endpoints
- Test both success and error cases
- Mock external services

## 🎨 Code Style

### Frontend Styling
- Use **Tailwind CSS** for styling
- Follow mobile-first approach
- Create reusable utility classes
- Maintain color palette consistency

### Backend API Design
- Follow **RESTful** principles
- Use meaningful HTTP status codes
- Return consistent JSON responses
- Document all endpoints

## 📖 Documentation

When adding new features, update:
- **README.md** - Overview of changes
- **API.md** - API endpoint documentation
- **Component documentation** - Usage examples
- **Inline comments** - Complex logic explanation

## 🐛 Bug Reports

When reporting bugs:
1. Check if the issue already exists
2. Provide clear description
3. Include reproduction steps
4. Share error messages & logs
5. Mention your environment (OS, Node version, etc.)

## 🔄 Pull Request Process

1. **Before submitting:**
   - Run `npm run lint` and fix issues
   - Run `npm run format` to format code
   - Run `npm run test` and ensure all tests pass
   - Update documentation

2. **Submit PR:**
   - Clear title following conventional commits
   - Describe changes in detail
   - Link related issues using `#issue-number`
   - Include screenshots for UI changes

3. **PR Template:**
   ```markdown
   ## Description
   Brief description of changes

   ## Type of Change
   - [ ] Bug fix
   - [ ] New feature
   - [ ] Breaking change
   - [ ] Documentation update

   ## Testing
   Describe testing performed

   ## Screenshots (if applicable)
   Add screenshots for UI changes

   ## Checklist
   - [ ] Code follows style guidelines
   - [ ] Tests pass
   - [ ] Documentation updated
   - [ ] No breaking changes
   ```

4. **Review & Merge:**
   - Maintainers will review your PR
   - Address feedback & suggestions
   - PR merged once approved

## 🚀 Performance Guidelines

- Keep bundle size minimal
- Optimize images and assets
- Use code splitting
- Minimize database queries
- Implement caching where appropriate
- Monitor performance metrics

## 🔐 Security Guidelines

- Never commit sensitive data (API keys, passwords)
- Use environment variables for secrets
- Validate all user inputs
- Sanitize data before database operations
- Follow OWASP top 10 prevention practices
- Report security vulnerabilities privately

## 📚 Resources

- [API Documentation](./docs/API.md)
- [Architecture Guide](./docs/ARCHITECTURE.md)
- [Setup Instructions](./docs/SETUP.md)
- [Next.js Documentation](https://nextjs.org/docs)
- [Express.js Guide](https://expressjs.com/)
- [PostgreSQL Docs](https://www.postgresql.org/docs/)

## ❓ Questions?

- Open an issue with `question:` prefix
- Join our community discussions
- Email: dev@booeb.com

## 🎉 Recognition

Contributors are recognized in:
- GitHub contributors page
- CONTRIBUTORS.md file
- Release notes

## 📋 Development Checklist

Before submitting a PR:

- [ ] Code follows project style guide
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests pass locally
- [ ] No console errors/warnings
- [ ] No breaking changes to API
- [ ] Performance impact assessed

---

Thank you for contributing to Booeb.com! 🙌

**Happy coding!**
