---
'@mastra/core': patch
'@mastra/memory': patch
---

Fixed Gemini rejecting a replayed step after working memory was saved in a parallel tool call. When the removed `updateWorkingMemory` call carried the step's thought signature, the signature now moves to the step's first remaining tool call instead of being dropped.
