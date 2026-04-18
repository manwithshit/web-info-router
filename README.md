# Web Information Router (WIR)

A universal web information routing engine for multi-agent scenarios.

## Overview
WIR is a decision-making framework that helps AI agents navigate the complex landscape of web data retrieval. It ensures your agents always use the fastest, most reliable, and most cost-effective method to get the information they need.

## Key Components
- **Decision Tree**: A multi-layered logic for tool selection.
- **Routing Table**: `routes.yaml` defines strategies for 70+ major platforms.
- **Skill Integration**: Standardized `SKILL.md` for seamless agent onboarding.

## Installation
1. Clone this repo into your agent's skill directory.
2. Install dependencies: `npm install -g @larksuite/cli`.
3. Configure your CDP Proxy if deep interaction is required.

## Usage
Agents should read `SKILL.md` to understand the routing logic and refer to `references/routes.yaml` for site-specific commands.
