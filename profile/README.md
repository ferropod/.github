<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-light.svg" />
    <img alt="ferropod — AI-Native PaaS in Pure Rust" src="https://raw.githubusercontent.com/ferropod/.github/main/assets/banner-dark.svg" width="100%" />
  </picture>
</p>

# ferropod

**AI-Native lightweight self-hosted PaaS in Pure Rust.**

Single binary + single `/data` directory. Zero external DB/MQ/S3/ELK/Node.js dependencies. Designed to run comfortably even on a **512 MiB RAM** VPS.

## Flagship Project

- [**ferropod/ferropod**](https://github.com/ferropod/ferropod) — Core single-binary PaaS engine built on **Axum**, **Turso (MVCC + `io_uring`)**, **Wasmtime**, and **MCP**.

## Core Capabilities

- **Workers & Static Sites**: Wasmtime (`wasi:http/incoming-handler@0.2.0`) with WIT Host Bindings + zero-overhead static asset hosting (SPA fallback, Range, ETag/304).
- **Turso Database (MVCC)**: Dedicated isolated databases (`core.db`, `queue.db`, per-project `dbs/<id>.db`, daily rotating `logs/*.db`).
- **Native Streaming Blob Storage**: 5-endpoint HTTP Blob API (`PUT`/`GET`/`HEAD`/`DELETE`/`LIST`) with `HMAC-SHA256` presigned URLs and content-addressed files in `/data/blobs`.
- **Persistent Queue & KV**: Disk-backed durability, micro-batch ingestion, backpressure (`429`), lease recovery, exponential backoff, DLQ replay, and TTL cleanup.
- **Zero-Build Admin UI & Daily Logs**: Embedded HTML/HTMX dashboard at `/_admin` with SSE live tail.
- **Native MCP Server**: Built-in `rmcp` tools and resources for AI agents to deploy, inspect logs, test, and roll back safely.

## Roadmap

| Milestone | Scope | Status |
| --- | --- | --- |
| **M1** | Storage foundation (Turso MVCC + Blob FS), Blob API, static routing, daily logs, maintenance, `/_admin` shell, REST API, CLI | In Progress |
| **M2** | Wasmtime AOT `.cwasm` runtime, WIT host bindings, Queue/Cron HTTP dispatcher | Planned |
| **M3** | Native `rmcp` MCP server (`deploy_stack`, `worker_invoke`, `logs_query`, resource tools, audit trail) | Planned |
| **M4** | Production hardening, health checks & auto-rollback, alerting webhooks, release packaging | Planned |

## License

All repositories under `ferropod` are licensed under the **Apache License 2.0** unless noted otherwise.
