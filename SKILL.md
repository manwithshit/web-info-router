---
name: web-info-router
description: A universal web information routing engine for multi-agent scenarios. It helps agents decide the optimal path (OpenCLI, WebFetch, Jina, or CDP Proxy) to access web content based on site characteristics and anti-scraping measures. Use when an agent needs to: (1) Fetch structured data from 70+ sites via OpenCLI, (2) Parallelize information retrieval using multiple agents, (3) Bypass complex anti-scraping using CDP Proxy with existing login states.
---

# Web Information Router (WIR)

This skill provides a standardized decision tree for AI agents to retrieve web information efficiently and reliably.

## Core Principles
1. **OpenCLI First**: Always prefer OpenCLI for supported sites (70+) to get structured data in 1-3s.
2. **Parallel Retrieval**: For unknown or complex sites, use WebFetch, Jina, and CDP in parallel to ensure quality and speed.
3. **Login State Reuse**: Use CDP Proxy to reuse existing browser sessions for sites requiring authentication (e.g., Xiaohongshu, X).

## Decision Tree Layers

### Layer 0: OpenCLI Shortcut
Check [routes.yaml](references/routes.yaml) for site support.
- **Public sites**: Execute direct CLI command (e.g., `opencli 36kr news`).
- **Cookie sites**: Check Bridge connection, then execute with `--cookie`.

### Layer 1: Parallel Fetch
If no OpenCLI support, trigger parallel agents:
- **Strategy `light_first`**: WebFetch + Jina (for blogs, docs, news).
- **Strategy `login_first`**: CDP + Jina (for X, Xiaohongshu, WeChat).

### Layer 2: CDP Proxy Deep Interaction
For high anti-scraping sites, use CDP Proxy to:
- Reuse Chrome login states.
- Perform human-like actions (click, scroll, screenshot).

## Resource Reference
- **Routing Table**: See [routes.yaml](references/routes.yaml) for site-specific strategies.
- **Setup Guide**: Ensure `opencli` and `cdp-proxy` are installed in the agent's environment.
