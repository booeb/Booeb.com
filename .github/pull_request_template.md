name: Pull Request Template
description: Create a pull request

body:
  - type: markdown
    attributes:
      value: |
        Thank you for your contribution! Please fill out the information below.

  - type: input
    id: title
    attributes:
      label: PR Title
      description: Clear and descriptive title
      placeholder: "feat: add product comparison feature"
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe changes in this PR
      placeholder: "What does this PR do?"
    validations:
      required: true

  - type: textarea
    id: related_issues
    attributes:
      label: Related Issues
      placeholder: "Fixes #123, Related to #456"

  - type: textarea
    id: changes
    attributes:
      label: Changes
      description: Bullet list of changes
      placeholder: |
        - Change 1
        - Change 2
        - Change 3

  - type: textarea
    id: testing
    attributes:
      label: Testing
      description: How was this tested?
      placeholder: "Tested on..."

  - type: checkboxes
    id: checklist
    attributes:
      label: Checklist
      options:
        - label: Code follows style guidelines
          required: true
        - label: Tests added/updated
          required: true
        - label: Documentation updated
          required: true
        - label: No breaking changes
          required: true
        - label: Self-reviewed the code
          required: true
