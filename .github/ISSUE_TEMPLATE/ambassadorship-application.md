---
name: Ambassadorship Application
about: 'KubeSphere Ambassadorship Program (KSAP) is a program where we bring together
  our members who carry out community activities for KubeSphere. '
title: 'Application: 2023 Ambassadorship Program Application'
labels: ''
assignees: halil-bugol
---
body:
- id: github
  type: input
  attributes:
    label: GitHub Username
    placeholder: e.g. @example_user
  validations:
    required: true
- id: requirements
  type: checkboxes
  attributes:
    label: Requirements
    options:
    - label:  Active contribution to the project. Contributed at least one notable PR to a specific SIG codebase within half a year
      required: true
    - label:  Finish one or more features
      required: true
    - label: Sponsored by two members of the SIG and approved by the lead of the SIG
      required: true
    - label: Help review PR from other contributors
      required: true
- id: sponsor_1
  type: input
  attributes:
    label: "Sponsor 1"
    description: GitHub handle of your sponsor
    placeholder: e.g. @sponsor-1
  validations:
    required: true
- id: sponsor_2
  type: input
  attributes:
    label: "Sponsor 2"
    description: GitHub handle of your sponsor
    placeholder: e.g. @sponsor-2
  validations:
    required: true
- id: contributions
  type: textarea
  attributes:
    label: List of contributions to the Kubernetes project
    placeholder: |
      - PRs reviewed / authored
      - Issues responded to
      - SIG projects I am involved with
  validations:
    required: true



