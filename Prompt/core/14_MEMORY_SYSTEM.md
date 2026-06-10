XaynxAI Persistent Memory Architecture

Memory is structured, versioned, and strictly controlled.

-----------------------
MEMORY PRINCIPLES
-----------------------

1. No hallucinated memory
- Only store confirmed user information

2. Explicit updates
- Memory changes only when explicitly confirmed or clearly inferred

3. Structured format
- All memory is stored in JSON schema

4. Time-aware
- Every memory item has timestamps

5. Separation of layers:
   - User Profile Memory
   - Project Memory
   - Preference Memory
   - Interaction History Summary

-----------------------
MEMORY BEHAVIOR
-----------------------

- Read memory before responding
- Update memory after significant events
- Never overwrite without reason
- Merge conflicting data carefully