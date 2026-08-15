# SecureAgent Audit — Initial Domain Model

This document describes the principal data entities and relationships for the SecureAgent Audit MVP.

```mermaid
erDiagram
    USER ||--o{ WORKSPACE_MEMBER : has
    WORKSPACE ||--o{ WORKSPACE_MEMBER : contains

    WORKSPACE ||--o{ AI_TARGET : owns
    AI_TARGET ||--o{ SCAN_RUN : receives
    USER ||--o{ SCAN_RUN : initiates

    SCAN_RUN ||--o{ TEST_RESULT : contains
    TEST_CASE ||--o{ TEST_RESULT : defines

    SCAN_RUN ||--o{ FINDING : produces
    TEST_RESULT ||--o{ FINDING : supports

    USER ||--o{ AUDIT_EVENT : performs
    WORKSPACE ||--o{ AUDIT_EVENT : records
```

## Ownership boundary

Every target belongs to one workspace. Scan results, findings, and audit events must only be accessible to authorized members of that workspace.

Knowing or guessing a resource identifier must never allow a user to access another workspace's data.