---
'@mastra/core': patch
---

Fixed trace scoring not finding tool invocations in nested span structures. Previously, `scoreTraceBatch` and `transformTraceToScorerInputAndOutput` only looked for tool spans as direct children of the root `agent_run` span, causing `toolInvocations` to always be empty for real traces where tools are nested under `agent_run > model_generation > model_step > tool_call`. The scorer now recursively collects all `TOOL_CALL` and `MCP_TOOL_CALL` spans from descendants of the root agent span while excluding tools from nested sub-agent spans, maintaining temporal ordering by `startedAt` timestamp.
