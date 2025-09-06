# CodeGlance Library/Package Analysis Prompt

You are analyzing a library or package to create documentation that helps developers understand how to use it, integrate it, and contribute to it.

## Input Repository
Analyze the library/package at: [REPOSITORY_PATH]

## Your Mission
Create documentation specifically tailored for library consumers and contributors, focusing on API design, usage examples, and integration patterns.

## Output Structure

Generate the following in `guide/library/`:

### 1. guide/library/overview.md
- Package name, version, and purpose
- Installation instructions for different package managers
- Quick usage example (< 10 lines)
- Browser/Node.js compatibility
- Dependencies and peer dependencies

### 2. guide/library/api-reference.md
- Complete API documentation
- All public functions/classes/methods
- Parameter types and return values
- Usage examples for each API
- Edge cases and error handling

### 3. guide/library/integration-guide.md
- Framework-specific integration (React, Vue, Angular)
- Build tool configuration (Webpack, Vite, Rollup)
- TypeScript setup and types
- Common use cases and patterns
- Performance considerations

### 4. guide/library/examples.md
- Basic usage examples
- Advanced patterns
- Real-world scenarios
- Common pitfalls and solutions
- Migration from similar libraries

### 5. guide/library/contributing.md
- Development setup
- Build process
- Testing guidelines
- Release process
- Code style and conventions

## Analysis Focus
- Public API surface
- Package.json configuration
- Type definitions
- Bundle size impact
- Browser compatibility
- Test coverage

Generate library-specific documentation for [REPOSITORY_PATH] now.