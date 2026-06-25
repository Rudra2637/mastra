---
'@mastra/core': patch
---

Fixed license validation to filter out `"undefined"` and `"null"` string literals from `MASTRA_LICENSE_KEY` and `MASTRA_EE_LICENSE` environment variables. 

Previously, some container and serverless hosting environments would inject these string literals as default values when the environment variable was left empty. Mastra was interpreting them as real enterprise license keys and attempting to validate them, polluting the startup logs with noisy validation errors (`INVALID_KEY`). They are now correctly ignored, letting the framework start cleanly in open-source mode.
