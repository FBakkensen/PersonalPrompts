# Implementation Plan Generation Template for Business Central AL Projects

## Objective
Create a comprehensive, actionable implementation plan based on project requirements and documentation. This plan will serve as a roadmap for systematic development following Test-Driven Development (TDD) and Behavior-Driven Development (BDD) methodologies specifically tailored for Business Central AL projects.

## Instructions

### 1. Analysis Phase
- Review all available project documentation, requirements, and specifications in the `aiwork` folder and documentation in the `.aidocs` folder
- Identify key components, dependencies, and integration points with existing Business Central functionality
- Analyze the scope and complexity of the implementation, considering AL development patterns
- Determine custom functionality scope (focus tests only on custom logic, not standard BC functionality)
- Identify page actions, codeunit procedures, and table operations requiring testing

### 2. Plan Structure
Create a detailed implementation plan with the following characteristics:

#### Task Organization
- **Sequential Numbering**: Assign each task a unique sequential number (1, 2, 3, etc.)
- **Status Tracking**: Include a checkbox at the beginning of each task:
  - `[ ]` for tasks not yet started
  - `[X]` for completed tasks
- **Atomic Tasks**: Ensure each task focuses on a single, specific action or deliverable
- **Logical Ordering**: Arrange tasks in dependency order, with prerequisites completed before dependent tasks
- **TDD Phases**: Explicitly separate Red-Green-Refactor phases for each development task

#### Task Details
For each task, include:

1. **Clear Objective**: A concise description of what needs to be accomplished
2. **Actionable Prompt**: Specific instructions that can be used to guide implementation
3. **Acceptance Criteria**: BDD scenarios in Given-When-Then format with positive/negative scenarios and edge cases
4. **Dependencies**: Any prerequisite tasks or external dependencies
5. **Estimated Effort**: Relative complexity or time estimate
6. **Testing Requirements**: Comprehensive test planning covering unit tests, integration tests, and user acceptance tests

### 3. Development Methodology - TDD/BDD for Business Central AL

#### Test-Driven Development (TDD) Approach
- **Red Phase**: Write failing tests first before any implementation code
- **Green Phase**: Implement minimal code to make tests pass
- **Refactor Phase**: Improve code quality while maintaining test coverage
- **Test Structure**: Separate test apps from main functionality with proper app.json configuration
- **Procedure Visibility**: Use 'internal' procedures for test accessibility (not 'local')
- **Test Execution**: Reference Start-TDDWorkflow.ps1 script execution from project root

#### Behavior-Driven Development (BDD) Integration
- **Scenario Structure**: Use Given-When-Then format for all acceptance criteria
- **User Story Validation**: Include business value and user perspective
- **Edge Case Coverage**: Address both positive and negative scenarios
- **Page Action Testing**: Test actual page actions, not just underlying codeunit procedures

#### Business Central AL Specific Considerations
- **No External Dependencies**: Avoid Microsoft test library dependencies (Library - Job, Library - Warehouse, etc.)
- **Custom Test Libraries**: Create simplified test data creation procedures within existing test codeunits
- **Test Data Isolation**: Ensure tests don't interfere with each other or existing data
- **Standard BC Logic**: Focus tests only on custom functionality, not standard Business Central logic
- **App Structure**: Maintain clear separation between test and production code

### 4. Plan Format

```markdown
# Implementation Plan: [Project Name]

## Overview
[Brief description of the project and implementation scope]

## Prerequisites
- Business Central development environment setup
- AL Language extension installed
- Test app structure configured with proper app.json
- Start-TDDWorkflow.ps1 script available in project root
- [Additional setup requirements, tools, or dependencies]

## TDD/BDD Implementation Tasks

### Task 1: [Task Title] - RED PHASE (Write Failing Tests)
- [ ] **Objective**: Write comprehensive failing tests for [specific functionality]
- **Prompt**: Create test codeunit with failing test procedures for [functionality]
- **BDD Acceptance Criteria**:
  - **Given**: [Initial state/context]
  - **When**: [Action/trigger]
  - **Then**: [Expected outcome]
  - **Scenario 1 (Positive)**: [Happy path scenario]
  - **Scenario 2 (Negative)**: [Error/edge case scenario]
  - **Scenario 3 (Edge Case)**: [Boundary condition scenario]
- **Dependencies**: [List any prerequisite tasks]
- **Testing Requirements**:
  - Create test codeunit in test app
  - Use 'internal' procedures for test accessibility
  - Include custom test data creation (no external Microsoft libraries)
  - Test page actions directly, not just underlying procedures
- **Validation**: Tests fail as expected when run via Start-TDDWorkflow.ps1

### Task 2: [Task Title] - GREEN PHASE (Minimal Implementation)
- [ ] **Objective**: Implement minimal code to make tests pass
- **Prompt**: Create minimal implementation in main app to satisfy failing tests
- **BDD Acceptance Criteria**:
  - **Given**: Failing tests from previous task
  - **When**: Minimal implementation is added
  - **Then**: All tests pass without additional functionality
- **Dependencies**: Task 1 (RED PHASE) completed
- **Testing Requirements**:
  - Run Start-TDDWorkflow.ps1 to verify tests pass
  - Ensure no additional functionality beyond test requirements
  - Maintain separation between test and production code
- **Validation**: All tests pass with minimal implementation

### Task 3: [Task Title] - REFACTOR PHASE (Code Quality)
- [ ] **Objective**: Improve code quality while maintaining test coverage
- **Prompt**: Refactor implementation for better design, performance, and maintainability
- **BDD Acceptance Criteria**:
  - **Given**: Working implementation with passing tests
  - **When**: Code is refactored for quality improvements
  - **Then**: All tests continue to pass with improved code structure
- **Dependencies**: Task 2 (GREEN PHASE) completed
- **Testing Requirements**:
  - Continuous test execution during refactoring
  - No test modifications during refactor phase
  - Maintain 100% test coverage
- **Validation**: Tests pass and code quality metrics improve

### Task 4: [Integration Task Title]
- [ ] **Objective**: [Integration or additional functionality]
- **Prompt**: [Specific instructions for integration]
- **BDD Acceptance Criteria**:
  - **Given**: [Integration context]
  - **When**: [Integration action]
  - **Then**: [Integration outcome]
- **Dependencies**: [Previous TDD cycle tasks]
- **Testing Requirements**:
  - Integration tests for Business Central standard functionality interaction
  - User acceptance tests for complete workflows
  - Page action testing for UI interactions
- **Validation**: [Integration verification steps]

## Quality Assurance
- [ ] All TDD cycles completed (Red-Green-Refactor)
- [ ] Unit tests passing (custom functionality only)
- [ ] Integration tests passing
- [ ] User acceptance tests passing
- [ ] Page action tests passing
- [ ] Code review completed
- [ ] No external test library dependencies
- [ ] Test data isolation verified
- [ ] Documentation updated

## Test Execution Checklist
- [ ] Start-TDDWorkflow.ps1 executed successfully from project root
- [ ] Test app compiles without errors
- [ ] Main app compiles without errors
- [ ] All custom functionality tests pass
- [ ] No tests written for standard BC logic
- [ ] Test procedures use 'internal' visibility

## Deployment Checklist
- [ ] Main app deployment verified
- [ ] Test app deployment verified (development only)
- [ ] Integration with existing BC functionality validated
- [ ] [Additional environment-specific deployment steps]
```

### 5. Quality Standards

#### Completeness
- Ensure all requirements are addressed with TDD/BDD methodology
- Include setup, Red-Green-Refactor cycles, testing, and deployment phases
- Cover error handling and edge cases in BDD scenarios
- Address documentation and maintenance needs
- Include comprehensive test coverage for custom functionality only
- Verify Business Central AL specific considerations are addressed

#### Clarity
- Use precise, unambiguous language suitable for AL development
- Provide sufficient detail for TDD/BDD implementation
- Include Given-When-Then examples for acceptance criteria
- Avoid assumptions about Business Central or AL prior knowledge
- Specify test execution methods (Start-TDDWorkflow.ps1)

#### Consistency
- Maintain uniform formatting and structure across TDD phases
- Use consistent BDD terminology throughout (Given-When-Then)
- Ensure logical flow between Red-Green-Refactor cycles
- Verify no conflicting requirements between test and production code
- Maintain consistent approach to test data creation and isolation

#### TDD/BDD Compliance
- Verify test-first approach is maintained throughout
- Ensure proper separation of test and production code
- Confirm 'internal' procedure visibility for test accessibility
- Validate no external Microsoft test library dependencies
- Check that page actions are tested directly, not just underlying procedures

### 6. Review Process
After creating the initial plan:

1. **Completeness Check**: Verify all requirements are covered with TDD/BDD approach
2. **TDD Cycle Validation**: Ensure proper Red-Green-Refactor sequence for each feature
3. **BDD Scenario Review**: Confirm Given-When-Then format with positive/negative/edge cases
4. **Dependency Validation**: Ensure proper task ordering respecting TDD phases
5. **AL Compliance Check**: Verify Business Central AL specific requirements
6. **Test Strategy Review**: Confirm focus on custom functionality, not standard BC logic
7. **Feasibility Review**: Confirm tasks are realistic and achievable within AL constraints
8. **Consistency Audit**: Check for conflicts or contradictions in test approach
9. **Clarity Assessment**: Ensure instructions are clear and actionable for AL developers

### 7. Output Requirements
- Save the plan as `implementationplan.md` in the `.aiwork` project folder
- Use proper Markdown formatting for readability and IDE compatibility
- Include a table of contents for longer plans
- Ensure the plan is version-controlled and trackable
- Structure content to avoid IDE warnings when used as a prompt template
- Include clear TDD phase indicators and BDD scenario formatting

## Success Criteria
The implementation plan is considered successful when:
- All project requirements are systematically addressed using TDD/BDD methodology
- Red-Green-Refactor cycles are clearly defined and actionable
- BDD scenarios cover positive, negative, and edge cases in Given-When-Then format
- Tasks are clearly defined and actionable for Business Central AL development
- Dependencies are properly identified and ordered respecting TDD phases
- Testing strategy focuses on custom functionality with proper test isolation
- Business Central AL specific considerations are integrated throughout
- The plan can be followed by any qualified AL developer
- Progress can be tracked and measured effectively through checkbox completion
- Test execution via Start-TDDWorkflow.ps1 is properly integrated
- Backward compatibility is maintained while extending existing workflows
