name: Feature Request
description: Suggest a new feature or enhancement
labels: ['enhancement', 'feature-request']
body:
  - type: markdown
    attributes:
      value: |
        Thank you for suggesting an enhancement! Please describe the feature clearly.

  - type: input
    id: title
    attributes:
      label: Feature Title
      placeholder: "e.g., Add wish list functionality"
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe the feature you'd like
      placeholder: "What new feature would you like to see?"
    validations:
      required: true

  - type: textarea
    id: use_case
    attributes:
      label: Use Case
      description: What problem does this solve?

  - type: textarea
    id: benefits
    attributes:
      label: Expected Benefits
      description: How would this benefit users?

  - type: checkboxes
    id: priority
    attributes:
      label: Priority
      options:
        - label: 'Low'
        - label: 'Medium'
        - label: 'High'
        - label: 'Critical'
