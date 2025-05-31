name: Pull Request
description: Submit a new prompt or improvement to an existing one
title: ""
labels: []
assignees: []

body:
  - type: markdown
    attributes:
      value: |
        Thank you for contributing to the AI Prompts collection! Please fill out the following information to help us review your contribution.

  - type: dropdown
    id: pr_type
    attributes:
      label: Type of Change
      description: What type of change does this PR introduce?
      options:
        - New prompt
        - Prompt improvement
        - Documentation update
        - Bug fix
        - Template update
        - Other (please describe)
    validations:
      required: true

  - type: input
    id: prompt_name
    attributes:
      label: Prompt Name(s)
      description: Which prompt(s) does this PR affect?
      placeholder: e.g., "Email Responder, Meeting Notes Generator"
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Description
      description: Describe your changes in detail
      placeholder: |
        - What changes did you make?
        - Why did you make these changes?
        - How do these changes improve the prompt(s)?
    validations:
      required: true

  - type: textarea
    id: testing
    attributes:
      label: Testing
      description: How did you test your changes?
      placeholder: |
        - Which AI models did you test with?
        - What scenarios did you test?
        - Any issues or limitations discovered?
    validations:
      required: true

  - type: checkboxes
    id: checklist
    attributes:
      label: Checklist
      description: Please confirm you have completed the following
      options:
        - label: I have read the CONTRIBUTING.md guidelines
          required: true
        - label: I have tested the prompt with at least one major AI model (GPT-4, Claude, Gemini)
          required: true
        - label: I have followed the prompt template format
          required: true
        - label: I have included appropriate tags and metadata
          required: true
        - label: I have provided clear examples of input and output
          required: true
        - label: The prompt works as intended and produces useful results
          required: true

  - type: textarea
    id: additional_notes
    attributes:
      label: Additional Notes
      description: Any other information for reviewers
      placeholder: Special considerations, future improvements, related issues...
