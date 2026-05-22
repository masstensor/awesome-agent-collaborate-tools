# Awesome Agent Collaboration Tools [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools and infrastructure for AI agent-to-agent communication, coordination, and collaboration.

Unlike general "awesome agents" lists that focus on *what agents can do*, this list focuses on **how agents work together** — the communication protocols, messaging systems, orchestration frameworks, shared memory layers, identity/trust mechanisms, and observability tools that make multi-agent systems possible.

**2026 context:** MCP has 97M+ downloads, A2A is adopted by 150+ organizations, and multi-agent systems are entering production at scale. This list tracks the infrastructure layer that makes it all work.

## Contents

- [Communication Protocols](#communication-protocols)
- [Messaging & Notification](#messaging--notification)
- [Multi-Agent Orchestration](#multi-agent-orchestration)
- [State & Memory](#state--memory)
- [Identity & Trust](#identity--trust)
- [Observability & Debugging](#observability--debugging)
- [Developer Tools & SDKs](#developer-tools--sdks)
- [Examples & Demos](#examples--demos)
- [Learning Resources](#learning-resources)

---

## Communication Protocols

Standards and protocols that define how agents discover, communicate, and delegate tasks to each other.

- [MCP (Model Context Protocol)](https://modelcontextprotocol.io) - Open standard by Anthropic for connecting AI models to tools and data sources. Governed by Linux Foundation. 97M+ downloads. The de facto standard for agent-to-tool communication.
- [A2A (Agent-to-Agent Protocol)](https://a2a-protocol.org) - Open protocol by Google (donated to Linux Foundation, June 2025) for peer-to-peer agent coordination. 150+ supporting organizations. Peer-to-peer agent communication and task delegation via Agent Cards.
- [ACP (Agent Communication Protocol)](https://agentcommunicationprotocol.dev) - RESTful agent interoperability protocol originated by IBM/BeeAI, donated to Linux Foundation. Enables agents built with different frameworks (LangChain, CrewAI, AutoGen, etc.) to communicate via a standardized API.
- [ANP (Agent Network Protocol)](https://agent-network-protocol.com) - Decentralized protocol for open agent networks, built on W3C DID standards. Enables agents to discover and interact without centralized coordination.
- [UTCP (Universal Tool Calling Protocol)](https://github.com/universal-tool-calling-protocol/utcp-agent) - Exposes tools to models using the tool's native endpoint rather than requiring an MCP wrapper. Contributed to Linux Foundation alongside ACP.
- [OpenAI Agents SDK — Handoffs](https://platform.openai.com/docs/guides/agents) - First-class agent-to-agent handoff primitives in OpenAI's Agents SDK. Allows agents to delegate tasks with full context transfer.

---

## Messaging & Notification

Real-time messaging, pub/sub, event streaming, and notification infrastructure designed for or applicable to agent-to-agent communication.

- [IM for Agents](https://im.fengdeagents.site) ⭐ - Agent-to-agent messaging without MCP. Three HTTP calls and your agents are talking — no SDK, no protocol implementation, no infrastructure setup. Cross-framework: Claude, GPT, Gemini, and local LLMs can all join the same room via REST API. Free tier available.
- [im-agents-mcp](https://github.com/masstensor/im-agents-mcp) - MCP server for IM for Agents. Allows any MCP-compatible agent to send and receive messages from other agents via IM for Agents.
- [Agent Notify Action](https://github.com/masstensor/agent-notify-action) - GitHub Action for sending notifications from automated agents to humans or other systems. Supports Telegram, Slack, and webhooks.
- [NATS](https://nats.io) - High-performance, cloud-native messaging system. Subjects and consumer groups make it excellent for agent event streaming and task routing. Supports request-reply patterns common in agent architectures.
- [Redis Pub/Sub + Streams](https://redis.io/docs/manual/pubsub/) - Battle-tested message patterns. Redis Streams provide persistent, consumer-group-based messaging ideal for agent pipelines where replay and backpressure matter.
- [RabbitMQ](https://www.rabbitmq.com) - Mature message broker with flexible routing (topics, fanout, headers). Useful for agent task queues with acknowledgment and retry semantics.
- [Apache Kafka](https://kafka.apache.org) - Distributed event streaming platform. Best for high-throughput, durable agent event logs and audit trails in large-scale multi-agent deployments.
- [XMTP](https://xmtp.org) - Decentralized, end-to-end encrypted messaging protocol. Used for agent-to-agent messaging with cryptographic identity, especially in Web3 agent contexts.

---

## Multi-Agent Orchestration

Frameworks for defining agent roles, task delegation, coordination logic, and workflow execution across multiple agents.

- [CrewAI](https://github.com/crewAIInc/crewAI) - Role-based multi-agent framework. Agents have roles, goals, and backstories. Simple API, production-ready, 30K+ GitHub stars.
- [LangGraph](https://github.com/langchain-ai/langgraph) - Graph-based agent orchestration by LangChain. Fine-grained control over agent state machines. Best for complex branching and human-in-the-loop flows.
- [AutoGen](https://github.com/microsoft/autogen) - Microsoft's framework for conversational multi-agent workflows. Strong support for human-in-the-loop, code generation, and group chat patterns.
- [Google ADK (Agent Development Kit)](https://google.github.io/adk-docs/) - Google's official SDK for building agents that work with Gemini and A2A protocol. Includes built-in support for multi-agent delegation.
- [Anthropic Agent SDK](https://docs.anthropic.com/en/docs/agents) - Official Anthropic toolkit for building Claude-powered agents with tool use, multi-turn conversations, and agent handoffs.
- [OpenAI Agents SDK](https://platform.openai.com/docs/guides/agents) - OpenAI's production agent framework (evolved from Swarm). Built-in support for tool use, handoffs, guardrails, and tracing.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - Microsoft's open-source SDK for building AI agents and copilots. Supports agent-to-agent patterns via the Process Framework.
- [Swarms](https://github.com/kyegomez/swarms) - Production-grade swarm orchestration. Supports hierarchical, sequential, concurrent, and mixture-of-agents patterns. Battle-tested for enterprise deployments.
- [AgentScope](https://github.com/modelscope/agentscope) - Alibaba's multi-agent platform. Provides MsgHub and pipeline abstractions for efficient message routing between agents.
- [Mastra](https://github.com/mastra-ai/mastra) - TypeScript-first agent framework with memory, tool-calling, workflows, and RAG. Designed for building production AI applications with multi-agent capabilities.
- [smolagents](https://github.com/huggingface/smolagents) - Hugging Face's minimal, code-centric agent framework. Agents write and execute Python code to achieve goals. Simple integration into multi-agent pipelines.
- [open-multi-agent](https://github.com/JackChen-me/open-multi-agent) - Production-grade multi-agent orchestration. Model-agnostic, supports team collaboration, task scheduling, and inter-agent communication with shared memory.
- [PydanticAI](https://github.com/pydantic/pydantic-ai) - Production-grade agent framework from the Pydantic team. Type-safe tool calling, dependency injection, and structured output. Supports multi-agent orchestration via agent handoff primitives.
- [LlamaIndex Workflows](https://docs.llamaindex.ai/en/stable/module_guides/workflow/) - Event-driven, async multi-agent orchestration built into LlamaIndex. Define agents as workflow steps with typed events — clean model for complex agent DAGs.
- [Dify](https://github.com/langgenius/dify) - Open-source LLM app platform with visual agent builder. Supports multi-agent workflows, tool integration, and knowledge retrieval. 60K+ GitHub stars.

---

## State & Memory

Tools for persisting agent context, shared knowledge, cross-session memory, and distributed state management.

- [Mem0](https://github.com/mem0ai/mem0) - Adaptive memory layer for AI agents. Intelligently compresses history into optimized memory representations. Claims up to 80% prompt token reduction. Lowest integration friction for standalone memory.
- [Zep](https://github.com/getzep/zep) - Long-term memory store with temporal knowledge graph. Tracks how facts change over time. Integrates structured business data with conversational history. Best for temporal-aware production pipelines.
- [Letta (formerly MemGPT)](https://github.com/cpacker/MemGPT) - Agents with OS-style virtual memory management. Self-editing memory architecture with in-context vs archival storage. Includes REST API and development environment.
- [Cognee](https://github.com/topoteretes/cognee) - Knowledge-graph-first memory for agents. Builds structured knowledge graphs from unstructured data for rich semantic retrieval.
- [LangMem](https://github.com/langchain-ai/langmem) - LangChain's memory abstraction layer. Multiple memory types (episodic, semantic, procedural) with a unified API.
- [Supermemory](https://github.com/supermemoryai/supermemory) - Universal memory API for AI agents. Import from anywhere, query with semantic search. Designed as a "memory backbone" across multiple agents.
- [Redis (State Management)](https://redis.io) - Fast in-memory store for short-term agent state, session data, and distributed locks. Essential for stateful multi-agent systems requiring sub-millisecond access.
- [Chroma](https://github.com/chroma-core/chroma) - Open-source embedding database. The most popular vector store for agent memory. Simple API, runs locally or in the cloud. pip install chromadb.
- [Qdrant](https://github.com/qdrant/qdrant) - High-performance vector database written in Rust. Excellent for production agent long-term memory with filtering, payload indexing, and sparse vector support.
- [Weaviate](https://github.com/weaviate/weaviate) - Open-source vector database with built-in vectorization. Modules for text, images, and multi-modal memory. Native GraphQL API.
- [Pinecone](https://www.pinecone.io) - Managed vector database. Serverless option allows agents to query semantic memory with zero infrastructure. Widely used in production agent deployments.
- [Haystack DocumentStore](https://docs.haystack.deepset.ai/docs/document-store) - Pluggable document store interface for Haystack agents. Supports Elasticsearch, OpenSearch, Weaviate, Pinecone, and more. Uniform API across backends.

---

## Identity & Trust

Specifications and tools for establishing agent identity, authentication, and trust relationships between agents. The defining security challenge of 2026.

- [A2A Agent Cards](https://a2a-protocol.org/latest/topics/agent-discovery/) - A2A protocol standard for agent self-description. Agents publish capabilities, authentication requirements, and endpoints in a standardized JSON format. Enables dynamic agent discovery.
- [SPIFFE / SPIRE](https://spiffe.io) - Production-grade workload identity framework. Each agent gets a cryptographically verifiable SVID (SPIFFE Verifiable Identity Document) — no shared secrets. SPIRE handles issuance, rotation, and revocation. The current best practice for secure agent-to-agent mTLS.
- [WIMSE (Workload Identity and Minimal Secrets)](https://datatracker.ietf.org/doc/draft-ietf-wimse-arch/) - IETF working group standard for workload/agent identity in cloud environments. Combines SPIFFE, OAuth 2.0, and token exchange for agent delegation. First draft published 2025, actively developed 2026.
- [OAuth 2.0 for AI Agents](https://oauth.net/2/) - Using OAuth 2.0 / DPoP for agent-to-agent authorization. Best practice for agents calling APIs or other agents on behalf of users. IETF draft (draft-klrc-aiagent-auth-00) published March 2026.
- [DID (Decentralized Identifiers)](https://www.w3.org/TR/did-core/) - W3C standard for cryptographic agent identity without central authority. Used as the foundation for ANP and decentralized agent networks.
- [WorkOS](https://workos.com) - Enterprise identity and auth platform increasingly used for AI agent authorization. Fine-grained permissions, audit logs, and organization-level access control — applies cleanly to multi-agent systems where agents act on behalf of users.
- [Permit.io](https://permit.io) - Policy-based authorization for apps and agents. Define what agents are allowed to do via ReBAC/ABAC policies. Supports runtime policy updates without redeploy.
- [SSOJet](https://ssojet.com) - Simplifies Enterprise SSO, OIDC, SAML, and SCIM integration for modern B2B SaaS and AI applications..
---

## Observability & Debugging

Tools for tracing, monitoring, evaluating, and debugging multi-agent systems in production.

- [LangSmith](https://smith.langchain.com) - End-to-end observability platform for LLM/agent applications by LangChain. Tracing, evaluation, dataset management, and prompt experimentation.
- [Langfuse](https://github.com/langfuse/langfuse) - Open-source LLM observability (MIT license). Acquired by ClickHouse. 19 Fortune 50 clients. Full-featured: tracing, evaluations, prompt management, datasets.
- [Arize Phoenix](https://github.com/Arize-ai/phoenix) - Open-source LLM observability. Trace agent runs, visualize spans, and evaluate outputs locally or in the cloud. Built on OpenTelemetry.
- [AgentOps](https://github.com/AgentOps-AI/agentops) - Agent-specific observability and testing. Session replays, cost tracking, failure analysis, and compliance monitoring. Native integrations with CrewAI, AutoGen, LangChain.
- [Maxim AI](https://www.getmaxim.ai) - Agent quality and observability platform. Evaluation pipelines, red-teaming, and production monitoring for agentic workflows.
- [OpenTelemetry](https://opentelemetry.io) - Vendor-neutral observability framework. Use with [OpenLLMetry](https://github.com/traceloop/openllmetry) for LLM-specific spans and agent traces.
- [Weights & Biases Weave](https://weave-docs.wandb.ai) - W&B's LLM observability platform. Trace, evaluate, and monitor agent runs with rich visualization.
- [Traceloop / OpenLLMetry](https://github.com/traceloop/openllmetry) - OpenTelemetry-based LLM observability. Automatic instrumentation for LangChain, CrewAI, AutoGen, and 20+ frameworks. Sends traces to any OTel-compatible backend (Datadog, Grafana, etc.).
- [Helicone](https://github.com/Helicone/helicone) - Open-source LLM observability and caching proxy. Drop-in for OpenAI/Anthropic/Gemini. Per-request latency, cost, and error tracking with user-level attribution.
- [Honeyhive](https://honeyhive.ai) - Agent evaluation and monitoring platform. Dataset management, A/B testing for prompts, and production quality monitoring. Focus on multi-step agent workflows.

---

## Developer Tools & SDKs

SDKs, CLIs, and utilities that accelerate building multi-agent systems.

- [im-for-agents-python](https://github.com/masstensor/im-for-agents-python) - Python SDK for IM for Agents. Send and receive messages between agents with minimal boilerplate.
- [multi-agent-starter](https://github.com/masstensor/multi-agent-starter) - Starter template for building multi-agent applications with MCP, A2A, and IM for Agents integration out of the box.
- [Dapr](https://dapr.io) - Distributed Application Runtime. Service invocation, pub/sub, state management, and actor pattern — all as portable building blocks for agent microservices.
- [BeeAI Framework](https://github.com/i-am-bee/bee-agent-framework) - IBM's open-source agent framework powering the ACP protocol. Production-ready with tool use, memory, and structured output.
- [FastMCP](https://github.com/jlowin/fastmcp) - The fastest way to build MCP servers in Python. Decorator-based API similar to FastAPI. Used by tens of thousands of MCP server authors. Now part of the official MCP Python SDK.
- [Composio](https://github.com/composiohq/composio) - Managed tool integration platform for AI agents. 250+ pre-built integrations (GitHub, Slack, Notion, etc.) with auth management. Works with LangChain, CrewAI, AutoGen, and any agent framework.
- [Portkey AI Gateway](https://github.com/Portkey-AI/gateway) - Open-source AI gateway with fallbacks, retries, load balancing, and request routing across 200+ LLMs. Essential for multi-agent deployments that use multiple model providers.
- [LiteLLM](https://github.com/BerriAI/litellm) - Unified API for 100+ LLMs. Use the same code to call OpenAI, Anthropic, Gemini, Groq, Ollama. Simplifies multi-agent systems where different agents use different models.
- [instructor](https://github.com/jxnl/instructor) - Structured output extraction from LLMs using Pydantic. Critical for agent-to-agent communication with typed message schemas — ensures agents receive parseable, validated data.
- [Arcade AI](https://github.com/ArcadeAI/arcade-ai) - Managed tool execution platform for AI agents. Secure, sandboxed execution with auth flows for enterprise tools. Reduces the surface area for agent security incidents.

---

## Examples & Demos

Reference implementations and worked examples of multi-agent collaboration patterns.

- [a2a-examples](https://github.com/masstensor/a2a-examples) - Practical examples of A2A protocol agent communication. Covers agent discovery, task delegation, and streaming responses.
- [multi-agent-demo](https://github.com/masstensor/multi-agent-demo) - End-to-end demo of multiple agents collaborating via IM for Agents and MCP. Shows orchestrator + specialist agent pattern.
- [multi-agent-patterns](https://github.com/masstensor/multi-agent-patterns) - Common patterns for building multi-agent systems with code examples. Covers pipeline, fan-out, consensus, and critic patterns.
- [Google A2A Samples](https://github.com/google-a2a/a2a-samples) - Official Google samples for A2A protocol. Best starting point for understanding Agent Cards and task lifecycle.
- [AutoGen Examples](https://github.com/microsoft/autogen/tree/main/samples) - Microsoft's reference examples for AutoGen agent patterns including group chat and code execution.
- [LangGraph Multi-Agent Examples](https://github.com/langchain-ai/langgraph/tree/main/examples) - Official LangGraph examples covering supervisor, hierarchical, and collaborative multi-agent patterns with state management.
- [CrewAI Examples](https://github.com/crewAIInc/crewAI-examples) - Official CrewAI examples including trip planner, stock analysis, and game builder crews. Best starting point for role-based multi-agent systems.
- [IM for Agents — 3 curl demo](https://masstensor.github.io/im-for-agents/) - Minimal demo of agent-to-agent messaging with 3 HTTP calls — no SDK, no framework. Shows the baseline for any cross-framework agent coordination.

---

## Learning Resources

Articles, specs, and guides for understanding the multi-agent collaboration landscape.

- [A2A Protocol Specification](https://a2a-protocol.org/latest/) - Full A2A specification, concepts, and implementation guide.
- [MCP Documentation](https://modelcontextprotocol.io/docs) - Official MCP docs with quickstarts, tutorials, and server implementation guides.
- [MCP vs A2A: Complete Guide (2026)](https://dev.to/pockit_tools/mcp-vs-a2a-the-complete-guide-to-ai-agent-protocols-in-2026-30li) - Deep comparison of when to use MCP vs A2A vs ACP.
- [AI Agent Protocol Ecosystem Map 2026](https://www.digitalapplied.com/blog/ai-agent-protocol-ecosystem-map-2026-mcp-a2a-acp-ucp) - Visual overview of the complete agent protocol landscape.
- [Survey of Agent Interoperability Protocols](https://arxiv.org/html/2505.02279v1) - Academic survey covering MCP, ACP, A2A, and ANP.
- [120+ Agentic AI Tools Mapped (2026)](https://www.stackone.com/blog/ai-agent-tools-landscape-2026/) - Comprehensive landscape map across 11 agent tool categories.
- [4 Patterns AI Agents Use to Coordinate](https://masstensor.github.io/im-for-agents/blog-coordination-patterns.html) - Practical guide: shared files, MCP, Kafka, and REST messaging — when each pattern breaks in production.
- [The Agent Identity Playbook (2026)](https://www.strata.io/blog/agentic-identity/new-identity-playbook-ai-agents-not-nhi-8b/) - How to think about non-human identity (NHI) for AI agents in enterprise environments.
- [Securing AI Agents: The Defining Cybersecurity Challenge of 2026](https://www.bvp.com/atlas/securing-ai-agents-the-defining-cybersecurity-challenge-of-2026) - Bessemer VP analysis of the agent security landscape — permissions, secrets, and trust boundaries.

---

## Contributing

Submissions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

Only add tools that are:
- Actively maintained (last commit within 12 months, or commercially supported)
- Genuinely useful for agent-to-agent collaboration (not just "agent-adjacent")
- Open source, or have a meaningful free tier

---

*Maintained by [@masstensor](https://github.com/masstensor) · [IM for Agents](https://im.fengdeagents.site) — messaging infrastructure for AI agents*
