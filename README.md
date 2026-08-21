# ai-chassis

A system to bolt together real AIs, not just run LLMs.

## What this is

With self-hosted AI, there's a strong emphasis on the LLM itself as the
magic. With frontier models, this extends to the point of calling an
entire production system of many moving pieces "a model". A complete AI
system needs far more than just an LLM to deliver the value it promises.
At a minimum, you need a knowledge base that provides extra context
around what the user is asking about, and some basic ways to interact
with the world. After that, there may be many other things you can add
on for additional value (metrics, routing, user profile/memories, quotas,
the list goes on).

ai-chassis is a middleware engine that treats **a complete AI system** —
not a raw LLM — as the thing you define. It doesn't run inference
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

