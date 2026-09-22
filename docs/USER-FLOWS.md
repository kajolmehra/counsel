# User flows

```mermaid
flowchart TB
    Landing[Landing page] --> Services[Legal / HR services]
    Services --> Auth[Register or sign in]
    Auth --> Session[Protected session]
    Session --> Question[Submit question]
    Question --> Limit{Allowance or paid access}
    Limit -->|Allowed| Validate[Validate request]
    Limit -->|Blocked| Pay[Upgrade entitlement]
    Pay --> Limit
    Validate --> Response[Receive streamed response]
    Response --> Saved[Persist and review history]
    Saved --> FollowUp[Ask follow-up]
    FollowUp --> Question
```

## Conversation lifecycle

1. The visitor selects a service area and creates an account.
2. The API verifies the token and checks the user's remaining allowance or paid entitlement.
3. The server validates the request, calls the AI provider with a constrained prompt, and streams the response to the client.
4. The conversation is saved with usage metadata for the history view.
5. Upgrade/payment state changes the server-side entitlement; the UI reflects the new access level.
