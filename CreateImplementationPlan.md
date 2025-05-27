# Implementation Plan Generation Template

## Objective
Create a comprehensive, actionable implementation plan based on project requirements and documentation. This plan will serve as a roadmap for systematic development following best practices.

## Instructions

### 1. Analysis Phase
- Review all available project documentation, requirements, and specifications in the `aiwork` folder and documentation in the `.aidocs` folder
- Identify key components, dependencies, and integration points
- Analyze the scope and complexity of the implementation
- Determine the appropriate development methodology and testing approach

### 2. Plan Structure
Create a detailed implementation plan with the following characteristics:

#### Task Organization
- **Sequential Numbering**: Assign each task a unique sequential number (1, 2, 3, etc.)
- **Status Tracking**: Include a checkbox at the beginning of each task:
  - `[ ]` for tasks not yet started
  - `[X]` for completed tasks
- **Atomic Tasks**: Ensure each task focuses on a single, specific action or deliverable
- **Logical Ordering**: Arrange tasks in dependency order, with prerequisites completed before dependent tasks

#### Task Details
For each task, include:

1. **Clear Objective**: A concise description of what needs to be accomplished
2. **Actionable Prompt**: Specific instructions that can be used to guide implementation
3. **Acceptance Criteria**: Measurable criteria to verify successful completion
4. **Dependencies**: Any prerequisite tasks or external dependencies
5. **Estimated Effort**: Relative complexity or time estimate
6. **Testing Requirements**: Specific testing approach and validation steps

### 3. Development Methodology
- **Test-Driven Development (TDD)**: For code-related tasks, specify test-first approach
- **Behavior-Driven Development (BDD)**: Include user story validation where applicable
- **Code Organization**: Clearly separate test code from implementation code
- **Quality Assurance**: Include code review, testing, and validation steps

### 4. Plan Format

```markdown
# Implementation Plan: [Project Name]

## Overview
[Brief description of the project and implementation scope]

## Prerequisites
- [List any setup requirements, tools, or dependencies]

## Implementation Tasks

### Task 1: [Task Title]
- [ ] **Objective**: [Clear description of what needs to be done]
- **Prompt**: [Specific instructions for implementation]
- **Acceptance Criteria**:
  - [Criterion 1]
  - [Criterion 2]
- **Dependencies**: [List any prerequisite tasks]
- **Testing**: [Specify testing approach - unit tests, integration tests, etc.]
- **Validation**: [How to verify completion]

### Task 2: [Task Title]
[Continue with same format...]

## Quality Assurance
- [ ] Code review completed
- [ ] All tests passing
- [ ] Documentation updated
- [ ] Integration testing completed

## Deployment Checklist
- [ ] [Environment-specific deployment steps]
- [ ] [Validation in target environment]
```

### 5. Quality Standards

#### Completeness
- Ensure all requirements are addressed
- Include setup, implementation, testing, and deployment phases
- Cover error handling and edge cases
- Address documentation and maintenance needs

#### Clarity
- Use precise, unambiguous language
- Provide sufficient detail for implementation
- Include examples where helpful
- Avoid assumptions about prior knowledge

#### Consistency
- Maintain uniform formatting and structure
- Use consistent terminology throughout
- Ensure logical flow between tasks
- Verify no conflicting requirements

### 6. Review Process
After creating the initial plan:

1. **Completeness Check**: Verify all requirements are covered
2. **Dependency Validation**: Ensure proper task ordering
3. **Feasibility Review**: Confirm tasks are realistic and achievable
4. **Consistency Audit**: Check for conflicts or contradictions
5. **Clarity Assessment**: Ensure instructions are clear and actionable

### 7. Output Requirements
- Save the plan as `implementationplan.md` in the `.aiwork` project folder
- Use proper Markdown formatting for readability
- Include a table of contents for longer plans
- Ensure the plan is version-controlled and trackable

## Success Criteria
The implementation plan is considered successful when:
- All project requirements are systematically addressed
- Tasks are clearly defined and actionable
- Dependencies are properly identified and ordered
- Testing and quality assurance steps are integrated
- The plan can be followed by any qualified developer
- Progress can be tracked and measured effectively
