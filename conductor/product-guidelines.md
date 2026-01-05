# Product Guidelines

## Core Principles
1. **Stability First**: Prioritize the stability and continued operation of the existing application. New features must not break existing functionality.
2. **Consistency**: Adhere strictly to the established architectural patterns and coding conventions of the `UniGetUI` project. This ensures that new package managers (pnpm, pipx, uv) behave predictably and integrate seamlessly with the rest of the application.
3. **Imitation over Innovation**: When implementing the new package managers, replicate the structure, logic, and error handling of similar existing managers (e.g., mimic `Npm` for `pnpm`, `Pip` for `pipx/uv`) rather than reinventing the wheel. This minimizes the risk of introducing new bugs or inconsistencies.

## Implementation Strategy
- **Deep Analysis**: Before writing code, thoroughly investigate the implementation of `Npm`, `Pip`, and other relevant managers to understand their interfaces, dependency injection, and configuration handling.
- **Incremental Integration**: Implement one package manager at a time (e.g., start with `pnpm`, then `pipx`, then `uv`), verifying each completely before moving to the next.
- **Robust Testing**: Verify that the new managers work correctly in isolation and do not interfere with global application state or other managers.

## Architectural Alignment
- **Namespace & Directory Structure**: Place new manager implementations in `src/UniGetUI.PackageEngine.Managers.<ManagerName>`, following the pattern of existing managers.
- **Interfaces**: Ensure strict adherence to `IPackageManager`, `IPackageDetails`, and other core interfaces defined in `UniGetUI.PackageEngine.Interfaces`.
- **UI Integration**: Update the Dashboard, Settings, and any other UI components to recognize and support the new managers, following the established MVVM patterns.

## Development Workflow & Quality Standards
- **Branching Strategy**: All development MUST occur in a dedicated feature branch, separate from the main branch.
- **Atomic Commits**: Commits must be small, focused, and self-contained ("atomic"). Each commit should represent a single logical change.
- **Remote Synchronization**: Push commits frequently to the online GitHub fork to ensure backup and visibility.
- **Reversible Checkpoints**: Establish stable checkpoints (via tags or specific commits) before major changes to allow for easy rollback if needed.
- **Testing Gates**: Implement and pass tests (unit/integration) before advancing to the next stage of development. Code must be verifiable and robust ("enterprise-grade").