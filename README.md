# Van Schulist

> **Systems engineer specializing in low-latency agent infrastructure, Model Context Protocol gateways, and zero-dependency developer tools. Founder of [Existential Cloud](https://www.existentialcloud.ccwu.cc).**

[![Official Portal](https://img.shields.io/badge/Portal-existentialcloud.ccwu.cc-10b981?style=flat-square)](https://www.existentialcloud.ccwu.cc)
[![Live Simulator](https://img.shields.io/badge/Simulator-GitHub%20Pages-10b981?style=flat-square)](https://vanschulist.github.io/existentialcloud-portal/)
[![Flagship: mcp-mesh](https://img.shields.io/badge/Flagship-mcp--mesh%20v1.3.0-0ea5e9?style=flat-square)](https://github.com/VanSchulist/mcp-mesh)
[![Architecture: Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero%20(Pure%20Stdlib)-zinc?style=flat-square)](https://github.com/VanSchulist/mcp-mesh#architecture-decisions--standard-library-rationale)
[![Test Suite: 100% Pass](https://img.shields.io/badge/Tests-161%2F161%20Passed-10b981?style=flat-square)](https://github.com/VanSchulist/mcp-mesh/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](https://opensource.org/licenses/MIT)

---

## 💡 Engineering Philosophy & Existential Cloud

Modern coding agents are bottlenecked by context-window economics: connecting 6–10 Model Context Protocol (MCP) servers statically dumps 10,000 to 32,000 tokens of heavy JSON schemas into every prompt before the user types a single word.

At **Existential Cloud**, I engineer zero-dependency developer infrastructure that treats LLM attention windows, process memory, and local compute resources with rigorous discipline:

* **Latency Distribution**: Inverted index keyword lookup $P50 \le 0.8\text{ms}$; subprocess IPC proxying $P50 \le 2.3\text{ms}, P99 \le 3.2\text{ms}$.
* **Context Efficiency**: Dynamic two-stage resolution slashes Turn-0 prompt bloat from 9,790 tokens to 527 tokens (94.6% reduction).
* **Pure Standard Library**: 100% standard library Python implementations (`concurrent.futures`, `json`, `sqlite3`, `http.server`, `subprocess`). Zero `pip install` dependency trees, zero supply-chain attack surface.

```text
 ┌────────────────────────────────────────────────────────────────────────┐
 │                      Heterogeneous AI Clients / IDEs                    │
 │               Claude Desktop  │  Cursor  │  Google Antigravity         │
 └───────────────────────────────────┬────────────────────────────────────┘
                                     │ stdio (JSON-RPC 2.0)
                                     │ Only 4 Meta-Tools Exposed (527 tokens, 94.6% reduction)
                                     ▼
 ┌────────────────────────────────────────────────────────────────────────┐
 │                   mcp-mesh v1.3.0 Federation Gateway                   │
 │  ┌──────────────────────────────────────────────────────────────────┐  │
 │  │        Federation Manager (Auto-discovery, Loop Prevention)       │  │
 │  ├──────────────────────────────────────────────────────────────────┤  │
 │  │      Tool Indexer, BM25 Scoring & Predictive Pre-Warmer          │  │
 │  ├──────────────────────────────────────────────────────────────────┤  │
 │  │  Circuit Breakers, Telemetry Ledger & Transparent Process Router │  │
 │  └──────────────────────────────────────────────────────────────────┘  │
 └───────────────────────────────────┬────────────────────────────────────┘
                                     │ Concurrently supervised upstream stdio pipes
         ┌───────────────────────────┼───────────────────────────┐
         ▼                           ▼                           ▼
 ┌───────────────────────┐   ┌───────────────────────┐   ┌───────────────────────┐
 │ ghost-job-hunter MCP  │   │ Postgres MCP          │   │ Filesystem / Git MCP  │
 │ (Antigravity Config)  │   │ (Claude Config)       │   │ (Cursor Config)       │
 └───────────────────────┘   └───────────────────────┘   └───────────────────────┘
```

---

## ⚡ 10-Second Zero-Install Developer Quickstarts

Run live demonstrations directly in your terminal without installing dependencies:

```bash
# 1. One-liner demonstration of mcp-mesh (50 tools across 6 mock MCP servers)
uvx --from git+https://github.com/VanSchulist/mcp-mesh mcp-mesh --demo

# 2. Start universal heterogeneous federation gateway across Claude, Cursor, and Antigravity
uvx --from git+https://github.com/VanSchulist/mcp-mesh mcp-mesh run --federate

# 3. Run instant deterministic heuristic audit of phantom job listings
uvx --from git+https://github.com/VanSchulist/ghost-job-hunter ghost-job-hunter --demo
```

---

## 📦 Open Source Portfolio (1 + 3 + N Architecture)

| Project | Role | Description | Stack & Status |
| :--- | :--- | :--- | :--- |
| [**`mcp-mesh`**](https://github.com/VanSchulist/mcp-mesh) | **FLAGSHIP** | Universal Heterogeneous MCP Reverse Proxy & Federation Gateway. Slashes Turn-0 prompt bloat by 85–95%, auto-discovers client configs, pre-warms target processes, and persists SQLite telemetry. | `Python 3.10+ Stdlib` • **v1.3.0** |
| [**`mcp-mesh-ui`**](https://github.com/VanSchulist/mcp-mesh-ui) | **OBSERVABILITY** | Real-time topology visualizer & telemetry dashboard for `mcp-mesh`. Features dark-mode local Web SPA (port 8765, SSE live stream), ANSI terminal TUI, and JSON-RPC inspection drawer. | `Vanilla JS / Web SPA` • **v1.3.0** |
| [**`mcp-registry-cli`**](https://github.com/VanSchulist/mcp-registry-cli) | **PACKAGE MGR** | Zero-config community package manager & synchronizer for MCP servers across Google Antigravity, Claude Desktop, and Cursor. | `Python CLI` • **v1.1.0** |
| [**`mcp-mesh-eval`**](https://github.com/VanSchulist/mcp-mesh-eval) | **BENCHMARK** | Frontier benchmark harness evaluating tool selection accuracy, TTFT latency, and Turn-0 token savings across 60 enterprise tools. | `Python Benchmark` • **v1.0.0** |
| [**`ghost-job-hunter`**](https://github.com/VanSchulist/ghost-job-hunter) | **TACTICAL AGENT** | Deterministic heuristic engine detecting phantom job postings, scraping live hiring feeds, auditing GitHub codebases, and managing a local SQLite opportunity pipeline. | `Python / SQLite / MCP` • **v2.1.0** |
| [**`career-reboot-armor`**](https://github.com/VanSchulist/career-reboot-armor) | **TACTICAL MANUAL** | Publication-grade field manual and portfolio strategy guide for engineers re-entering the tech workforce after extended leave or caregiving. | `Markdown / DOCX Release` • **v1.0.0** |
| [**`github-ai-studio`**](https://github.com/VanSchulist/github-ai-studio) | **GOVERNANCE** | Central engineering lab, Architectural Decision Records (ADRs), research tracker, and multi-agent ecosystem governance. | `Architecture Hub` • **Active** |

---

## 🛠️ Systems Standards

* 🚀 **Zero External Dependencies**: All core libraries and CLI tools are engineered strictly with the Python standard library. Runs anywhere without `pip install` friction or dependency breakage.
* 🧠 **Context-Window Discipline**: AI agents should never parse 50 static schemas at Turn 0. Compact signatures and lazy on-demand resolution save API cost and eliminate attention degradation.
* 🛡️ **Defensive Reliability**: Automated circuit breakers with cooldown timers, non-blocking notification semantics, and 100% passing test suites across ecosystem (161/161 tests passing).

---

## 🌐 Links & Contact

* **Official Portal**: [www.existentialcloud.ccwu.cc](https://www.existentialcloud.ccwu.cc)
* **GitHub Profile & Repos**: [@VanSchulist](https://github.com/VanSchulist)
* **License**: All public software released under the [MIT License](https://opensource.org/licenses/MIT).
