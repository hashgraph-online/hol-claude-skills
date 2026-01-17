# HOL Claude Skills

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | A lightweight SDK providing reference implementations for Hashgraph Consensus Standards (HCS) created by Hashgraph Online.<br><br>This SDK is built and maintained by [Hashgraph Online](https://hashgraphonline.com), a consortium of leading Hedera Organizations within the Hedera ecosystem.<br><br>[📚 Standards SDK Documentation](https://hashgraphonline.com/docs/libraries/standards-sdk/)<br>[📖 HCS Standards Documentation](https://hashgraphonline.com/docs/standards) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |


[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Claude Code slash commands for [Hashgraph Online (HOL)](https://hol.org) development - search agents, resolve UAIDs, and chat with AI agents on Hedera.

## What is this?

This repository provides Claude Code slash commands that enable AI-assisted interaction with the HOL Registry. These commands use the real RegistryBrokerClient API from @hashgraphonline/standards-sdk.

## What is HOL?

[Hashgraph Online (HOL)](https://hol.org) is an open-source SDK ecosystem for AI agents on Hedera:

- **[Standards SDK](https://github.com/hashgraph-online/standards-sdk)** - TypeScript SDK with RegistryBrokerClient
- **[Registry](https://hol.org/registry)** - Universal agent discovery
- **[MCP Server](https://github.com/hashgraph-online/hashnet-mcp-js)** - AI assistant integration

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

## Resources

- [HOL Website](https://hol.org)
- [HOL Registry](https://hol.org/registry)
- [Standards SDK Docs](https://hol.org/docs/libraries/standards-sdk/overview/)
- [Registry Broker Client](https://hol.org/docs/libraries/standards-sdk/registry-broker-client/)
- [GitHub](https://github.com/hashgraph-online)

## License

MIT License - see [LICENSE](LICENSE) for details.
