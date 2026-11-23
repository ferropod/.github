<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-light.svg" />
    <img alt="ferropod — AI-Native PaaS in Pure Rust" src="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-dark.svg" width="100%" />
  </picture>
</p>

# ferropod

[![Docs](https://img.shields.io/badge/Docs-ferropod.github.io-1f2937.svg)](https://ferropod.github.io)
[![CI](https://github.com/ferropod/ferropod/actions/workflows/ci.yml/badge.svg)](https://github.com/ferropod/ferropod/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/ferropod/ferropod?include_prereleases&label=Release)](https://github.com/ferropod/ferropod/releases)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache--2.0-orange.svg)](https://github.com/ferropod/ferropod/blob/main/LICENSE)

**AI-Native lightweight self-hosted PaaS in Pure Rust.**

Single binary + single `/data` directory. Zero external DB/MQ/S3/ELK/Node.js dependencies. Designed to run comfortably even on a **512 MiB RAM** VPS.

## Repositories

| Repository | Description |
| --- | --- |
| [**ferropod/ferropod**](https://github.com/ferropod/ferropod) | Core single-binary PaaS engine built on **Axum**, **Turso (MVCC + `io_uring`)**, **Wasmtime**, and native **Pure Rust MCP**. |
| [**ferropod/ferropod.github.io**](https://github.com/ferropod/ferropod.github.io) | Official homepage and 6-language documentation site ([ferropod.github.io](https://ferropod.github.io)). |

## Core Capabilities

- **Workers, Static Sites & Declarative Deploys**: Wasmtime AOT `.cwasm` runtime with strongly typed WIT host bindings (`ferropod:platform@0.2.0`), zero-overhead static asset hosting (SPA fallback, byte `Range`, `ETag`/`304`), and declarative `ferropod.toml` / `ferropod deploy` workflows.
- **Gateway & Built-in HTTPS**: Automatic Let's Encrypt HTTPS (`TLS-ALPN-01`) or manual PEM certificates, dynamic reverse proxy, Basic Auth, rate limiting, canary traffic splits, and health-check-verified promote/auto-rollback.
- **Turso MVCC Databases, KV, Queues, Cron & Blob Storage**: Isolated databases (`core.db`, `kv.db`, `queue.db`, `search.db`, per-project `dbs/<id>.db`, daily `logs/*.db`), DB FTS, mandatory-TTL & ephemeral KV, 4-tier peak-shaving queues with DLQ replay, Cron scheduler, and 5-endpoint streaming Blob API (`PUT`/`GET`/`HEAD`/`DELETE`/`LIST`) with `HMAC-SHA256` presigned URLs.
- **Built-in AI Gateway & Hybrid Search**: OpenAI-compatible proxy (`/_ai/v1/chat/completions`, `/_ai/v1/embeddings`) with primary/fallback failover, response caching, RPM limits, and monthly token budgets—plus Turso dense vector + BM25 hybrid search (`search.db`).
- **Native Pure Rust MCP Server & Agent Discovery**: Shared Streamable HTTP (`POST /_mcp`) and CLI stdio (`ferropod mcp`) transports exposing 10 high-semantic tools and 2 resources with RBAC scopes and audit logging, alongside unauthenticated `GET /_api/v1/openapi.json` and `GET /_api/v1/llms.txt`.
- **Zero-Build Admin Console & Operations**: 6-language Admin Console at `/_panel`, SSE live logs, Prometheus metrics (`/_api/v1/metrics/prometheus`), alerting webhooks, consistent snapshots (`ferropod snapshot`), cgroup-aware sizing profiles (`auto` / `low-mem` / `standard`), and one-click self-update.

## Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/ferropod/ferropod/main/scripts/install.sh | sudo bash
```

## Milestones

| Milestone | Scope | Status |
| --- | --- | --- |
| **M1** | Storage foundation (Turso MVCC + Blob FS), Blob API, static routing, daily logs, maintenance, `/_panel` shell, REST API, CLI | Completed |
| **M2** | Wasmtime AOT `.cwasm` runtime, WIT host bindings (`ferropod:platform@0.2.0`), Queue/Cron worker dispatch, local HTTP proxy | Completed |
| **M3** | Native Pure Rust MCP server (`/_mcp` HTTP & `ferropod mcp` stdio, 10 tools, 2 resources, RBAC & audit trail), OpenAPI & `llms.txt` | Completed |
| **M4** | AI Gateway, Vector + BM25 Hybrid Search, built-in HTTPS (ACME), canary/health-check rollback, alerts, snapshots, 6-language UI, self-update & releases | Completed |

## Documentation & Links

- **Homepage & Docs** (`en` / `简体中文` / `繁體中文` / `日本語` / `한국어` / `Español`): <https://ferropod.github.io>
- **Getting Started**: <https://ferropod.github.io/docs/getting-started.html>
- **MCP Server Guide**: <https://ferropod.github.io/docs/mcp.html>
- **HTTP API Reference**: <https://ferropod.github.io/docs/api-reference.html>
- **WIT Host Binding Contract**: [`wit/platform.wit`](https://github.com/ferropod/ferropod/blob/main/wit/platform.wit)
- **Architecture Spec**: [`docs/ARCHITECTURE.md`](https://github.com/ferropod/ferropod/blob/main/docs/ARCHITECTURE.md)
- **Releases**: <https://github.com/ferropod/ferropod/releases>
- **Discussions**: <https://github.com/ferropod/ferropod/discussions>

## License

All repositories under `ferropod` are licensed under the **Apache License 2.0** unless noted otherwise.
