# Contributing to WSO2 Integrator: BI

Thank you for your interest in contributing to WSO2 Integrator: BI! This guide will help you understand how to contribute to different parts of the project.

## Repository Overview

This repository (`product-ballerina-integrator`) is primarily used for **issue tracking** for the WSO2 Integrator: BI product. The actual development happens in separate repositories:

### Frontend Development
The frontend code is located in the **WSO2 VS Code Extensions monorepo**:
- **Repository**: https://github.com/wso2/vscode-extensions
- **Architecture**: Rush.js monorepo with multiple workspaces
- **Workspaces**:
  - `workspaces/ballerina` - Core Ballerina extension ecosystem (20+ packages)
  - `workspaces/bi` - Ballerina Integrator specific frontend features
  - `workspaces/common-libs` - Shared libraries and utilities

### Backend Development
The backend is powered by the **Ballerina Language Server**:
- **Repository**: https://github.com/ballerina-platform/ballerina-language-server
- **Protocol**: Language Server Protocol (LSP) for IDE integration
- **Features**: Auto-completion, diagnostics, hover, go-to-definition, code actions

## Development Setup

### Prerequisites
Recommended to refer the https://github.com/wso2/vscode-extensions/#prerequisites for frontend prerequisites (including Node.js >= 22 and Rush CLI installation) and for the backend refer to the [Ballerina Language Server repository](https://github.com/ballerina-platform/ballerina-language-server) for setup instructions. 

### Frontend Development Setup

#### Initial Setup
```bash
# Clone the repository
git clone https://github.com/wso2/vscode-extensions.git
cd vscode-extensions

# Install Rush CLI globally (if not already installed)
npm install -g @microsoft/rush

# Install dependencies
rush install

# Build all packages
rush build
```

#### Workspace Structure
- **Main Extension**: `workspaces/ballerina/ballerina-extension/`
- **Visual Components**: `workspaces/ballerina/ballerina-visualizer/`
- **Core Libraries**: `workspaces/ballerina/ballerina-core/`
- **RPC Client**: `workspaces/ballerina/ballerina-rpc-client/`
- **Diagram Components**: `workspaces/ballerina/sequence-diagram/`, `workspaces/ballerina/type-diagram/`, etc.
- **BI Workspace**: `workspaces/bi/`

#### Development Commands
```bash
# Build specific extensions
rush build --to ballerina

# Watch mode for development (from individual package directories)
cd workspaces/ballerina/ballerina-visualizer
npm start

# E2E testing
cd workspaces/bi/bi-extensions
npm run e2e-test
```

### Backend Development Setup

#### Initial Setup
```bash
# Clone the language server repository
git clone https://github.com/ballerina-platform/ballerina-language-server.git
cd ballerina-language-server

# Follow the build instructions in the repository
# Typically involves Java development environment setup
```

#### Language Server Features
- **Auto Completion**: Context-aware code completion
- **Hover Provider**: Type information and documentation
- **Signature Help**: Function parameter hints
- **Go to Definition**: Navigate to symbol definitions
- **Diagnostics**: Real-time error and warning reporting
- **Code Actions**: Quick fixes and refactoring suggestions
- **Go to Implementation**: Find interface implementations

## How to Contribute

### Reporting Issues
- **All issues** (frontend, backend, documentation, etc.) should be reported in **this repository**
- Use the GitHub issue tracker to submit bug reports, feature requests, and general questions
- Please search existing issues before creating new ones to avoid duplicates
- Follow the issue templates when available

### Code Contributions

#### Frontend Contributions
1. **Fork** the [vscode-extensions](https://github.com/wso2/vscode-extensions) repository
2. **Setup** your development environment using the steps above
3. **Navigate** to the appropriate workspace:
   - For core Ballerina functionality: `workspaces/ballerina`
   - For BI-specific features: `workspaces/bi`
4. **Development Guidelines**:
   - Follow existing code patterns and conventions
   - Use TypeScript with strict type checking
   - Implement proper error handling and logging
   - Write unit tests for new functionality
   - Update documentation for public APIs
   - Test with VS Code Extension Development Host (select `Ballerina & BI Extensions` from the debug menu and run it to view the extension development host)
5. **Testing Requirements**:
   - Navigate to `workspaces/bi/bi-extension`
   - E2E tests for UI changes: `npm run e2e-test`
6. **Build and Package**:
   - Verify build success: `rush build --to ballerina`
7. **Submit** a pull request to the main repository

#### Backend Contributions
1. **Fork** the [ballerina-language-server](https://github.com/ballerina-platform/ballerina-language-server) repository
2. **Setup** your development environment following the repository's build instructions
3. **Development Guidelines**:
   - Follow Java coding standards
   - Adhere to Language Server Protocol specifications
   - Implement comprehensive unit tests
   - Document public APIs and extension points
4. **Testing Requirements**:
   - All unit tests must pass
   - Integration tests for LSP features
   - Performance testing for large codebases
5. **Submit** a pull request to the main repository

### Development Best Practices

#### Code Quality
- **Type Safety**: Use TypeScript with strict mode enabled
- **Error Handling**: Implement proper error boundaries and logging
- **Performance**: Optimize for large codebases and real-time responsiveness
- **Accessibility**: Follow VS Code accessibility guidelines
- **Security**: Never commit secrets or sensitive information

#### Communication Patterns
- **Webview Communication**: Use vscode-messenger for webview-extension messaging
- **RPC Integration**: Use ExtendedLangClient for language server communication
- **State Management**: Use XState for complex UI state machines
- **Event System**: Implement proper event handling and cleanup

#### Testing Strategy
- **Unit Tests**: Test individual components and utilities in the language server
- **E2E Tests**: Test complete user workflows in VS Code

### Architecture Guidelines

#### Frontend Architecture
- **Modular Design**: Separate packages for different concerns
- **Shared Libraries**: Use common-libs for reusable components
- **Webview Components**: Build React components for visual features
- **Extension Logic**: Keep VS Code-specific logic in extension packages

#### Backend Architecture
- **LSP Compliance**: Implement standard Language Server Protocol features
- **Extension Points**: Design for extensibility and plugin architecture
- **Performance**: Optimize for real-time language analysis
- **Error Recovery**: Implement robust error handling and recovery

### Documentation
Documentation contributions are welcome! Please check the respective repositories for documentation-specific contribution guidelines.

## Getting Help

- **Documentation**: https://bi.docs.wso2.com/
- **Discord**: Join the [WSO2 community on Discord](https://discord.gg/wso2)
- **Community Library**: https://wso2.com/library/?area=integration

## Code of Conduct

Please note that this project follows WSO2's [Code of Conduct](https://wso2.com/code-of-conduct/). By participating in this project, you agree to abide by its terms.

## License

By contributing to WSO2 Integrator: BI, you agree that your contributions will be licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

---

For questions about contributing, feel free to reach out through any of the community channels listed above.