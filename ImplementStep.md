# AL/Business Central TDD/BDD Implementation Prompt

Please implement only the first uncompleted task from the TDD workflow implementation plan in `.aiwork\implementationplan.md` using Test-Driven Development (TDD) and Behavior-Driven Development (BDD) methodologies.

## Core Implementation Process

Follow this specific process for each task:

### 1. Task Identification and Analysis
- Read the implementation plan file to identify the first task that is NOT marked as completed (lacks a checked checkbox [x])
- Review any related documentation files in the `.aiwork` folder that provide additional context for that specific task
- Use the codebase-retrieval tool to gather detailed information about existing code that relates to the task before making any changes

### 2. Test-First Development (TDD Red Phase)
Before implementing any functionality:
- **Write failing tests first** in the test app that define the expected behavior
- Create test scenarios using Given-When-Then format for BDD clarity:
  - **Given**: Initial state/preconditions
  - **When**: Action or event that triggers the behavior
  - **Then**: Expected outcome or result
- Ensure tests fail initially (Red phase) to confirm they're testing the right behavior
- Place all test code in the designated test app, separate from production code

### 3. Code Structure and Accessibility
When implementing functionality:
- **Test App**: Contains all test codeunits, test pages, and test scenarios
- **Main App**: Contains actual business logic and functionality
- **Procedure Visibility**: Declare procedures as `internal` rather than `local` when they need to be accessible from external test applications
  - `local` procedures are only accessible within the same codeunit
  - `internal` procedures can be accessed by dependent apps including test apps
- Maintain clear separation between test and production code

### 4. Implementation (TDD Green Phase)
- Create a detailed implementation plan for just that one task, including which files need to be created or modified
- Implement the minimum code necessary to make the tests pass (Green phase)
- Focus on making tests pass without over-engineering the solution
- Ensure proper error handling and validation as defined in test scenarios

### 5. Refactoring (TDD Refactor Phase)
- Clean up and optimize the code while keeping tests passing
- Improve code structure, readability, and maintainability
- Ensure adherence to AL coding standards and best practices
- Verify that all tests continue to pass after refactoring

### 6. Test Execution and Validation
- **Execute tests using the TDD workflow script**: Run the `Start-TDDWorkflow.ps1` script from the root of the project
  - The script will compile and deploy both the main app and test app
  - The script will then automatically run the tests
  - Refer to `scripts\TDD-Workflow.md` for detailed documentation on the TDD workflow process
- Run all relevant tests to confirm the implementation works correctly
- Verify that new tests pass and existing tests remain unaffected
- Execute both unit tests and integration tests as applicable
- Document any test results or findings

### 7. Quality Assurance
- Fix any linter errors or warnings before considering the task complete
- Ensure code follows established coding standards
- Verify that the implementation meets all acceptance criteria defined in the task
- Confirm that error handling scenarios are properly tested

### 8. Documentation and Plan Updates
- Mark the task as completed by updating the checkbox from `[ ]` to `[x]` in the implementation plan
- Update any relevant documentation files in the `.aiwork` folder
- Review if any of the changes require updates to the implementation plan and update accordingly

## BDD Scenario Template

When creating test scenarios, use this template structure:

```
Scenario: [Brief description of the behavior being tested]
  Given [initial state or preconditions]
  When [action or event occurs]
  Then [expected outcome or result]
  And [additional expected outcomes if applicable]
```

## Test Organization Guidelines

### Test App Structure
- Create test codeunits for each functional area
- Use descriptive naming conventions for test procedures
- Group related test scenarios within the same test codeunit
- Implement setup and teardown procedures for test data management

### Test Data Management

#### Test Data Library Pattern
- **Create dedicated library codeunits** for each functional area following the naming convention `[AreaName] Test Data Library`
  - Examples: "Sales Test Data Library", "Purchase Test Data Library", "Inventory Test Data Library"
  - Each library codeunit should contain reusable test data creation procedures for its specific domain
  - Library codeunits promote consistency, reusability, and maintainability across test scenarios

#### Centralized Test Data Creation
- **Centralize all test data creation logic** in library codeunits rather than scattering it across individual test codeunits
- Each library should provide a comprehensive set of data creation procedures for its functional area
- Test codeunits should call library procedures rather than creating data directly
- This approach ensures consistent data patterns and reduces code duplication

#### Standardized Data Creation Procedures
Each library codeunit should provide standardized procedures for common test scenarios:
- **Minimal Data Procedures**: Create entities with only required fields (e.g., `CreateMinimalCustomer()`, `CreateMinimalItem()`)
- **Default Data Procedures**: Create entities with commonly used default values (e.g., `CreateCustomerWithDefaults()`, `CreateItemWithDefaults()`)
- **Complex Scenario Procedures**: Create entities for specific test scenarios (e.g., `CreateComplexSalesOrder()`, `CreateMultiLocationInventory()`)
- **Parameterized Procedures**: Allow customization of key fields while maintaining defaults for others

#### Data Isolation and Production Safety
- **Ensure complete isolation** from production data by using test-specific data patterns
- Use distinctive naming conventions or prefixes for test data (e.g., "TEST_", "AUTO_")
- Implement data validation to prevent accidental creation of production-like data
- Create test data in isolated number series or date ranges when applicable
- Verify that test data creation doesn't trigger production workflows or integrations

#### Test Data Cleanup Strategies
- **Implement cleanup patterns** appropriate to the test scope and Business Central constraints
- For unit tests: Clean up test data after each test procedure when feasible
- For integration tests: Consider cleanup at the test codeunit level or use transaction rollback patterns
- Document cleanup responsibilities clearly in test procedures
- Handle cleanup gracefully when data has dependencies or cannot be deleted
- Consider using temporary tables for data that doesn't need to persist beyond the test

#### Cross-Area Dependencies Management
- **Handle dependencies between functional areas** systematically in library codeunits
- Library codeunits may call other library codeunits to create prerequisite data
- Example: Sales Test Data Library may call Customer Test Data Library to ensure valid customer data exists
- Establish clear dependency hierarchies to avoid circular references
- Document dependencies between library codeunits
- Consider creating shared foundation data procedures for commonly needed entities

#### Library Codeunit Structure Guidelines
- **Organize procedures logically** within each library codeunit
- Group related procedures together (e.g., all customer-related procedures in one section)
- Use consistent parameter patterns across procedures in the same library
- Include comprehensive documentation for each procedure's purpose and parameters
- Implement error handling for data creation failures
- Provide both simple and complex variants of data creation procedures

#### Test Data Consistency Patterns
- **Maintain consistent data patterns** across all test scenarios
- Use the same library procedures across different test codeunits for the same type of data
- Establish conventions for test data values (dates, amounts, codes) to ensure predictable behavior
- Create data that supports both positive and negative test scenarios
- Ensure test data is realistic enough to validate business logic accurately

### Assertion Patterns
- Use clear, descriptive assertion messages
- Test both positive and negative scenarios
- Verify expected outcomes and side effects
- Include boundary condition testing where applicable

## Implementation Constraints

- **Single Task Focus**: Do NOT implement multiple tasks or move ahead to subsequent tasks
- **Test-First Approach**: Always write tests before implementing functionality
- **Separation of Concerns**: Maintain clear boundaries between test and production code
- **Quality Gates**: All tests must pass and linter errors must be resolved before task completion

## Final Review Checklist

Before returning to the user, ensure:
- [ ] All tests are passing (Green phase achieved)
- [ ] Code has been refactored for quality and maintainability
- [ ] Linter errors and warnings are resolved
- [ ] Task is marked as completed in the implementation plan
- [ ] Any necessary updates to subsequent tasks in the implementation plan are made
- [ ] Test coverage adequately validates the implemented functionality
- [ ] BDD scenarios clearly document the expected behavior

**Focus exclusively on completing the first uncompleted task thoroughly using TDD/BDD methodology.**
