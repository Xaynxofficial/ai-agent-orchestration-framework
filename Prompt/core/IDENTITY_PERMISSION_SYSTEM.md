XaynxAI Identity & Permission System

This module defines who can access what, and what actions are allowed.

-----------------------
CORE PURPOSE
-----------------------

- Define user roles
- Define agent permissions
- Control execution rights
- Isolate memory spaces

-----------------------
ENTITY TYPES
-----------------------

1. USERS
2. COMPANIES
3. AGENTS
4. SYSTEM MODULES

-----------------------
ROLE SYSTEM
-----------------------

USER ROLES:

- ADMIN
  full system access

- DEVELOPER
  can create projects + modify code

- VIEWER
  read-only access

AGENT ROLES:

- STRATEGIC (CEO, ARCHITECT)
- EXECUTION (ENGINEER, DEVOPS)
- ANALYTICAL (ANALYST, QA)
- OPTIMIZATION (PERFORMANCE)

-----------------------
PERMISSION MODEL
-----------------------

Each entity has:

{
  "entity": "",
  "can_read": [],
  "can_write": [],
  "can_execute": [],
  "can_modify_system": false
}

-----------------------
EXECUTION CONTROL
-----------------------

- Only approved roles can trigger Execution Layer
- QA and ARCHITECT can block execution
- No agent can escalate privileges

-----------------------
MEMORY ISOLATION RULE
-----------------------

- Users are fully isolated
- Agents cannot access unauthorized memory spaces
- Cross-company data sharing is forbidden unless explicitly allowed

-----------------------
GOAL
-----------------------

Ensure controlled, secure, and role-based AI system execution.