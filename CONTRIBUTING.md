# Contributing to ArtSpark

Thank you for your interest in contributing to ArtSpark! We welcome contributions from the community to help improve this AI-powered art project generator. Whether you're fixing bugs, adding features, improving documentation, or suggesting ideas, your help is appreciated.

Please take a moment to review this document to make the contribution process easy and effective for everyone involved.

## How to Contribute

### Reporting Bugs

If you find a bug:
1. Check if the issue already exists in the [Issues](https://github.com/decagondev/art-spark/issues) section.
2. If not, create a new issue with:
   - A clear title and description.
   - Steps to reproduce the bug.
   - Expected vs. actual behavior.
   - Screenshots or logs if applicable.
   - Your environment (e.g., Java version, OS).

Label the issue as "bug" for easier tracking.

### Suggesting Enhancements

For feature requests or improvements:
1. Open an issue in the [Issues](https://github.com/decagondev/art-spark/issues) section.
2. Describe the enhancement clearly.
3. Explain why it would be useful.
4. Reference relevant sections from `/docs/PRD.md` if applicable.

Label the issue as "enhancement".

### Pull Requests

We use a pull request (PR) workflow for code contributions. Follow these steps:

1. **Fork the Repository**:
   - Fork the repo on GitHub and clone your fork locally.

2. **Set Up Your Environment**:
   - Follow the setup instructions in [README.md](/README.md).
   - Install dependencies with `mvn clean install`.

3. **Create a Branch**:
   - Branch from `main`: `git checkout -b feature/your-feature` or `bugfix/your-bugfix`.
   - Keep branches focused on one change.

4. **Make Changes**:
   - Refer to `/docs/TASKS.md` for epics, PRs, and commits structure.
   - Follow code style guidelines (see below).
   - Update documentation if needed (e.g., `/docs/API.md` for API changes).
   - Add or update tests.

5. **Commit Your Changes**:
   - Use clear, descriptive commit messages (e.g., "Fix bug in AI model loading").
   - Reference issue numbers (e.g., "Closes #123").

6. **Push and Open a PR**:
   - Push to your fork: `git push origin your-branch`.
   - Open a PR against the `main` branch.
   - In the PR description:
     - Explain the changes.
     - Link to related issues.
     - Mention any breaking changes.
     - Provide testing instructions.

7. **Review Process**:
   - Maintainers will review your PR.
   - Be responsive to feedback and make necessary updates.
   - Once approved, your PR will be merged.

### Code Style Guidelines

- **Java**: Follow Google Java Style Guide (use Checkstyle if possible).
- **Indentation**: 4 spaces.
- **Naming**: CamelCase for classes/methods, snake_case for variables where appropriate.
- **Comments**: Use Javadoc for public methods; add inline comments for complex logic.
- **Dependencies**: Avoid adding new ones without discussion.
- **Error Handling**: Use proper exceptions and logging.

### Testing

- Write unit tests with JUnit and Mockito.
- Integration tests for controllers, services, and DB interactions.
- Aim for >80% code coverage (use JaCoCo).
- Run `mvn test` before submitting a PR.

### Documentation

- Update README.md for setup/user changes.
- Modify `/docs/CODE-SNIPPETS.md` for new code examples.
- Keep `/docs/API.md` current for API endpoints.

## First-Time Contributors

If you're new, look for issues labeled "good first issue" or "help wanted". Start small to get familiar with the codebase.

## Recognition

Contributors are credited in the [README.md](/README.md) or a CONTRIBUTORS file. Thanks for helping make ArtSpark better!

If you have questions, open an issue or contact the maintainers.

Happy contributing! 🎨
