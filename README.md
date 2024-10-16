# The 3 Commit Method
 The "3 Commit" Method (3CM) is a git workflow based on interface- and test- driven development for maintaining complex code at scale.

## Workflow Overview

This workflow ensures that each issue is addressed systematically with a focus on testing and code quality. It involves three main commits per issue, ensuring a clean and traceable history.

### Step-by-Step Process

1. **Create a GitHub Issue**
   - A user creates a GitHub issue, which could be a feature request or a bug report.

2. **Automatic Branch Creation**
   - A GitHub Action automatically creates a branch from the head of `main` named `issue-xxx`, where `xxx` is the issue number.
   - This branch is protected, and direct commits are not allowed. All changes must be made through Pull Requests (PRs), and only squash merging is permitted.

   ```mermaid
   graph TD;
       A[Create GitHub Issue] --> B[GitHub Action: Create issue-xxx Branch];
       B --> C[Protected Branch: issue-xxx];
   ```

3. **First PR: Failing Test Cases**
   - The first PR for the `issue-xxx` branch must contain only test cases for the feature or bug.
   - These test cases must fail initially, as the corresponding code should not be written yet.
   - Once reviewed and approved, this PR is squash merged, resulting in a single commit on the `issue-xxx` branch.

   ```mermaid
   graph TD;
       D[Write Failing Test Cases] --> E[Create First PR];
       E --> F[Review & Squash Merge];
       F --> G[Single Commit on issue-xxx];
   ```

4. **Second PR: Code Changes**
   - The second PR should include code changes that make the previously written test cases pass.
   - After the test cases pass and the PR is reviewed and approved, it is squash merged, forming the second commit on the `issue-xxx` branch.

   ```mermaid
   graph TD;
       H[Write Code to Pass Tests] --> I[Create Second PR];
       I --> J[Review & Squash Merge];
       J --> K[Second Commit on issue-xxx];
   ```

5. **Merge to Main**
   - Once the issue is resolved, a PR is raised to merge the `issue-xxx` branch into `main`.
   - The `main` branch is protected, requiring PRs for any merges.
   - After review and approval, the contents of the `issue-xxx` branch are squash merged into `main`, creating a single atomic commit with a reference to the issue number as `issue-xxx`. This is the third commit of the process.

   ```mermaid
   graph TD;
       L[Resolve Issue] --> M[Create PR to Merge into Main];
       M --> N[Review & Squash Merge];
       N --> O[Single Atomic Commit on Main];
   ```

## Benefits

- **Traceability**: Each issue is linked to a specific set of commits, making it easy to track changes.
- **Quality Assurance**: The workflow enforces test-driven development, ensuring that code changes are verified by tests.
- **Clean History**: Squash merging keeps the commit history clean and focused on meaningful changes.

## Conclusion

The "3 Commit" Method provides a structured approach to handling issues in a codebase, emphasizing testing and code quality while maintaining a clean and traceable commit history.
