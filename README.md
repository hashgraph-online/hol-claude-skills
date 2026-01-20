# HOL Claude Skills

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | **Claude Code slash commands for the Universal Agentic Registry.** Search 59,000+ AI agents, resolve UAIDs, and chat with agents across NANDA, MCP, A2A, Virtuals, and more.<br><br>[📚 SDK Documentation](https://hol.org/docs/libraries/standards-sdk/)<br>[📖 API Documentation](https://hol.org/docs/registry-broker/) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

[![npm version](https://img.shields.io/npm/v/@hashgraphonline/standards-sdk?style=for-the-badge&logo=npm&logoColor=white&label=standards-sdk)](https://www.npmjs.com/package/@hashgraphonline/standards-sdk)
[![Run in Postman](https://img.shields.io/badge/Run_in-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99%26entityType%3Dcollection%26workspaceId%3Dfb06c3a9-4aab-4418-8435-cf73197beb57)
[![OpenAPI Spec](https://img.shields.io/badge/OpenAPI-3.1.0-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)](https://hol.org/registry/api/v1/openapi.json)

[![Open in CodeSandbox](https://img.shields.io/badge/Open_in-CodeSandbox-blue?style=for-the-badge&logo=codesandbox&logoColor=white)](https://codesandbox.io/s/github/hashgraph-online/hol-claude-skills)
[![Open in StackBlitz](https://img.shields.io/badge/Open_in-StackBlitz-1269D3?style=for-the-badge&logo=stackblitz&logoColor=white)](https://stackblitz.com/github/hashgraph-online/hol-claude-skills)
[![Open in Gitpod](https://img.shields.io/badge/Open_in-Gitpod-FFAE33?style=for-the-badge&logo=gitpod&logoColor=white)](https://gitpod.io/#https://github.com/hashgraph-online/hol-claude-skills)

## What is the Universal Registry?

The [Universal Agentic Registry](https://hol.org/docs/registry-broker/) is the connectivity layer for the autonomous web. One standards-compliant API to access agents from:

| Protocol | Description |
|----------|-------------|
| **Virtuals** | Tokenized AI agents |
| **A2A** | Google's Agent-to-Agent protocol |
| **MCP** | Anthropic's Model Context Protocol |
| **ERC-8004** | On-chain agent verification |
| **x402 Bazaar** | Agent payment rails |
| **OpenConvAI** | Conversational AI standard |
| **XMTP** | Decentralized messaging |
| **ANS** | Agent Name Service |

## Installation

```bash
# Clone and copy commands to your project
git clone https://github.com/hashgraph-online/hol-claude-skills.git
cp -r hol-claude-skills/.claude/commands your-project/.claude/
```

Or download individually:

```bash
mkdir -p .claude/commands
curl -o .claude/commands/hol-search.md https://raw.githubusercontent.com/hashgraph-online/hol-claude-skills/main/.claude/commands/hol-search.md
```

## Available Commands

### `/hol-search`

Search the HOL Registry for agents:

```
/hol-search weather agents
/hol-search "scheduling assistant" --registry hcs-10
```

### `/hol-resolve`

Resolve an agent by UAID:

```
/hol-resolve hcs10://0.0.123456/my-agent
```

### `/hol-stats`

Get registry statistics:

```
/hol-stats
/hol-stats registries
/hol-stats protocols
```

### `/hol-chat`

Chat with an agent:

```
/hol-chat hcs10://0.0.123456/agent "Hello!"
```

## SDK Methods Used

All commands use the real RegistryBrokerClient API:

| Command | SDK Method |
|---------|------------|
| `/hol-search` | `client.search(params)` |
| `/hol-resolve` | `client.resolveUaid(uaid)` |
| `/hol-stats` | `client.stats()`, `client.registries()` |
| `/hol-chat` | `client.chat.start()`, `conversation.sendMessage()` |

## Environment Variables

For chat functionality:

```bash
HOL_API_KEY=your-api-key
HEDERA_OPERATOR_ID=0.0.123456
HEDERA_OPERATOR_KEY=302e...
```

## API & Documentation

| Resource | Link |
|----------|------|
| **Live Registry** | [hol.org/registry](https://hol.org/registry) |
| **API Documentation** | [hol.org/docs/registry-broker](https://hol.org/docs/registry-broker/) |
| **SDK Reference** | [hol.org/docs/libraries/standards-sdk](https://hol.org/docs/libraries/standards-sdk/) |
| **Postman Collection** | [Run in Postman](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99) |
| **OpenAPI Spec** | [openapi.json](https://hol.org/registry/api/v1/openapi.json) |
| **npm Package** | [@hashgraphonline/standards-sdk](https://www.npmjs.com/package/@hashgraphonline/standards-sdk) |

## Related Repositories

- [`standards-sdk`](https://github.com/hashgraph-online/standards-sdk) - The core SDK powering the registry client
- [`hol-cursorrules`](https://github.com/hashgraph-online/hol-cursorrules) - Cursor AI rules for HOL development
- [`hol-claude-md`](https://github.com/hashgraph-online/hol-claude-md) - CLAUDE.md templates for HOL projects

## 🏆 Score HOL Points

Contribute to this repository and score [HOL Points](https://hol.org/points)! 

- 🔧 **Fix bugs** or improve documentation
- ✨ **Add new features** or examples
- 📝 **Submit pull requests** to score points

Points can be used across the HOL ecosystem. [Learn more →](https://hol.org/points)

## License

MIT License - see [LICENSE](LICENSE) for details.
