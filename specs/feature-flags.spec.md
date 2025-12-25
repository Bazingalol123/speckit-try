# Feature Flag Service – Functional Specification

## Goal
Provide a backend service for managing feature flags with environment support and percentage rollout.

## Functional Requirements

### Feature Flags
- A feature flag has:
  - id (string)
  - name
  - description
  - enabled (boolean)
  - rollout_percentage (0–100)
  - environments: dev, prod

### API
- Create a feature flag
- Update a feature flag
- Delete a feature flag
- Get all feature flags
- Evaluate a feature flag for a given user id

### Evaluation Rules
- If flag is disabled → return false
- If enabled and rollout_percentage = 100 → return true
- If enabled and rollout_percentage < 100:
  - Hash user id
  - Deterministically decide if user is inside rollout

### Non-Functional Requirements
- REST API
- JSON responses
- Simple persistence (SQLite or in-memory)
- Include unit tests
- Clear folder structure
