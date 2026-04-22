---
name: loginuser
description: Execute loginUser tool.
---

# loginuser

## When to use
Use this skill when the user intent maps to `loginuser` and the user is asking for actionable data retrieval or an operation that this tool can perform.

Use this skill over generic alternatives when:
- The user request explicitly mentions data/entities handled by this tool.
- The required parameters can be derived from the current conversation.
- A deterministic API call is preferable to free-form reasoning.

Do not use this skill when:
- The user intent is unrelated to this tool's domain.
- Required identifiers are missing and cannot be inferred.
- Another tool has a closer semantic match.

## Parameter Mapping
1. Read the MCP schema for `loginuser` and list required vs optional parameters.
2. Map user-provided values to schema keys exactly.
3. For missing required fields, ask a concise clarification question.
4. Normalize values (IDs, enums, date/time formats) before calling the tool.

## Step-by-Step Execution
1. Analyze the user intent.
2. Determine the required parameters based on the MCP schema.
3. Build the final argument object with validated types.
4. Call the `loginuser` MCP tool with the correct parameters.
5. Parse and summarize the API response in user-focused language.

## Failure Handling
- If validation fails: explain which field is invalid and request only the missing/fixed values.
- If API returns 4xx: reflect the business error and suggest a corrective next step.
- If API returns 5xx/timeouts: communicate temporary failure and offer retry.
- If response is empty: explicitly state no results and suggest broader or alternate inputs.

## Worked Example
- User intent: "Run `loginuser` for my latest record and show key fields only."
- Action: Resolve the required identifier, call `loginuser`, extract the top-level summary fields.
- Response style: short summary first, then bullet list of key values.

## Pro Tips
- Prefer explicit parameter values over assumptions.
- Keep tool outputs concise; include raw payload only when user asks.
- If multiple results are returned, prioritize the most recent or most relevant item and mention selection logic.
