# ai-chassis

A system to bolt together real AIs, not just run LLMs.

## What this is

Most AI tooling treats the LLM call as "the product" and treats everything
else — retrieval/RAG, MCP tool orchestration, plugin management, memory —
as peripheral infrastructure bolted onto whichever layer owns the
user-facing surface (usually the chat UI). Frontier AI products don't work
that way: they're a coherent system, not an LLM with extras stapled on.
There's no equivalent reference architecture for self-hosted setups.

ai-chassis is a middleware engine that treats **a complete AI system** —
not a single LLM call — as the thing you define. It doesn't run inference
itself; client apps call its API, requests pass through a configurable
pipeline of middleware (RAG, memory, tool orchestration, etc., each running
as its own process rather than engine-native code), and the engine forwards
the resulting request to an inference backend (Ollama, vLLM, or a
third-party provider). The V1 goal is for that whole assembled system —
which middleware, in what order, configured how, talking to which
backend — to export/import as a single portable TOML config file.

Full design spec: [DESIGN.md](./DESIGN.md).

## Status

**No code has been written yet.** This repository currently contains
design documentation only. Architecture, config schema, middleware
execution substrate, and API shape are all open/unresolved — see
[DESIGN.md](./DESIGN.md) for the current thinking and open questions.

