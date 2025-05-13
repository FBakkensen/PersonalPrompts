# AL & Business Central Coding Instructions

## Key Principles

- Write clear, technical responses with precise AL examples.
- Use Business Central's built-in features and tools wherever possible to leverage its full capabilities.
- Prioritize readability and maintainability; follow AL coding conventions and Business Central best practices.
- Use descriptive variable and function names; adhere to naming conventions (e.g., PascalCase for public members, camelCase for private members).
- Structure your project in a modular way using Business Central's object-based architecture to promote reusability and separation of concerns.

## AL/Business Central

- Use table objects for defining data structures and page objects for user interfaces.
- Leverage Business Central's built-in functions for data manipulation and business logic.
- Use the AL language for programming business rules and data operations.
- Utilize codeunits for encapsulating and organizing business logic.
- Follow the object-oriented programming paradigm in AL for clear separation of concerns and modularity.
- Use AL's trigger system for responding to events and user actions.

## Error Handling and Debugging

- Implement error handling using try-catch blocks where appropriate, especially for database operations and external service calls.
- Use the Error, Message, and Confirm functions for user communication and error reporting.
- Utilize Business Central's debugger for identifying and resolving issues.
- Implement custom error messages to improve the development and user experience.
- Use AL's assertion system to catch logical errors during development.

## Dependencies

- Microsoft Dynamics 365 Business Central
- Visual Studio Code with AL Language extension
- AppSource apps (as needed for specific functionality)
- Third-party extensions (carefully vetted for compatibility and performance)

## Business Central-Specific Guidelines

- Use table extensions and page extensions for modifying functionality on dependent objects.
- Use report extensions for modifying functionality on depending reports.
- Keep business logic in codeunits; use the Visual Studio Code for object development and initial setup.
- Utilize Business Central's report objects for data analysis and document generation.
- Apply Business Central's permission sets and user groups for security management.
- Use Business Central's built-in testing framework for unit testing and integration testing.
- Leverage Business Central's data upgrade codeunits for efficient data migration between versions.
- Use Business Central's dimensions for flexible data analysis and reporting.
- Object Names must Start with the prefix used in the project.
- Object Names must be in PascalCase.
- Object Names must not be longer than 30 characters.

## Performance Optimization

- Optimize database queries by using appropriate filters and table relations.
- Implement background tasks using job queue entries for long-running operations.
- Use AL's FlowFields and FlowFilters for calculated fields to improve performance.
- Optimize report performance by using appropriate data items and filters.

## Tooltips
- All fields should have tooltips to provide context and guidance to users.
- Use the `Tooltip` property in AL to define tooltips for fields, actions, and controls.
- Ensure tooltips are concise and informative, helping users understand the purpose and usage of each field or action.
- Avoid overly technical jargon in tooltips; aim for clarity and simplicity.
- Use consistent terminology and phrasing across tooltips to maintain a cohesive user experience.
- Review and update tooltips regularly to ensure they reflect any changes in functionality or user interface.
- Tooltips on fields must start with 'Specifies' to maintain consistency and clarity.

## Key Conventions

1. Follow Business Central's object-based architecture for modular and reusable application elements.
2. Prioritize performance optimization and database management in every stage of development.
3. Maintain a clear and logical project structure to enhance readability and object management.

## Variables and Parameters
- Names of Variables and parameters of type `Record` should be suffixed with the table name. without whitespaces.
- Names of Variables and parameters of type `Page` should be suffixed with the page name. without whitespaces.
- This is Wrong examples:
```al
JobRecordJob: Record Job;
JobPage: Page Job;
```

This is Right examples:
```al
Job: Record Job;
Job: Page Job;
```

- If there is a used for multiple variables or parameters of the same type, the name must be suffixed with a meaningful name.
- A paremeter must only be declared as var if nessecary.

## Coding Style
- Use 4 spaces for indentation.
- Use PascalCase for object names, variables, and parameters.
- Only use Begin End for compund statements.
- Use `if` statements without `begin` and `end` for single-line conditions.
- Use Record.IsEmpty() instead of Record.FindSet() or Record.FindFirst() if the queried record is not used.

> **Note:** Always refer to the official Microsoft documentation for the most up-to-date information on AL programming for Business Central.
> [Business Central AL Programming Documentation (Japanese)](https://learn.microsoft.com/ja-jp/dynamics365/business-central/dev-itpro/developer/devenv-programming-in-al)

## Object Type Specific Instructions

### page
- The layout must be defined before the actions.
- Identifiers of fields and actions must not be prefixed.
- The properties `Promoted` and `PromotedCategory` must not be used for actions, instead use the actionref syntax.
- The identifier for a promoted actionref must have a suffix of `_Promoted`.

### pageextension
- The layout must be defined before the actions.
- Identifiers must be prefixed with the prefix used in the project.
- Tooltips should be on table fields not on the page fields.
- Fields must have an ApplicationArea property set to `All`.
- The properties `Promoted` and `PromotedCategory` must not be used for actions, instead use the actionref syntax.
- The identifier for a promoted actionref must have a suffix of `_Promoted`.

### table
- Fields on tables must have a Dataclassification property set to `ToBeClassified`.
- Identifiers on Fields on tables should not have a prefix.
### tableextension
- Identifiers must be prefixed with the prefix used in the project, the prefix must always end with a space.
- Fields must have a Dataclassification property set to `ToBeClassified`.

### codeunits
- Procedures must only be marked with `[Scope('OnPrem')]` if this are explicitly stated.
- Procedures must follow the the Single Responsibility Principle (SRP).
- Check for IsGuiAllowed() before using any GUI functions.
- For major functionality create a codeunits with the name of the functionality. Thhese codeunits must follow this pattern:

```al
codeunit 71115696 "NALJP Calc. Usage Total Cost"
{
    procedure CalculateUsageTotalCostCosts(var JobTask: Record "Job Task")
    var
        Handled: Boolean;
    begin
        OnBeforeCalculateUsageTotalCostCosts(JobTask, Handled);
        DoCalculateUsageTotalCostCosts(JobTask, Handled);
        OnAfterCalculateUsageTotalCostCosts(JobTask);
    end;

    local procedure DoCalculateUsageTotalCostCosts(var JobTask: Record "Job Task"; var Handled: Boolean)
    var
        Job: Record Job;
    begin
        if Handled then
            exit;

        Job.Get(JobTask."Job No.");

        if (not Job."NALJP Compl. pct. Rcogn. Cost") or (Job."NALJP Completion" = 0) then
            exit;

        JobTask."Recognized Costs Amount" := JobTask."Schedule (Total Cost)" * (Job."NALJP Completion" / 100);

        Handled := true;
    end;

    [BusinessEvent(false)]
    local procedure OnBeforeCalculateUsageTotalCostCosts(var JobTask: Record "Job Task"; var Handled: Boolean)
    begin
    end;

    [BusinessEvent(false)]
    local procedure OnAfterCalculateUsageTotalCostCosts(var JobTask: Record "Job Task")
    begin
    end;
}
```

- For small functionality create a codeunits with the name of the functionality and the suffix `Mgt`.

