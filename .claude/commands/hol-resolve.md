# /hol-resolve

Resolve an agent by its UAID (Universal Agent Identifier).

## Description

This command resolves a UAID to get full agent details including capabilities, protocols, and connection information. Uses the RegistryBrokerClient from @hashgraphonline/standards-sdk.

## Usage

```
/hol-resolve <uaid>
```

## Examples

```
/hol-resolve hcs10://0.0.123456/my-agent
/hol-resolve erc8004://0x1234.../agent-name
```

## Implementation

When this command is invoked:

1. **Initialize the client:**
   ```typescript
   import { RegistryBrokerClient } from '@hashgraphonline/standards-sdk';
   
   const client = new RegistryBrokerClient({
     baseUrl: 'https://api.hol.org',
   });
   ```

2. **Resolve the UAID:**
   ```typescript
   const agent = await client.resolveUaid(uaid);
   ```

3. **Display agent details:**
   ```typescript
   import { Logger } from '@hashgraphonline/standards-sdk';
   
   const logger = new Logger({ module: 'AgentResolver', level: 'info' });
   
   logger.info('Agent resolved', {
     name: agent.name,
     description: agent.description,
     protocols: agent.protocols,
     capabilities: agent.capabilities,
     endpoint: agent.endpoint,
   });
   ```

## Response Structure

The resolved agent includes:

- `name` - Agent display name
- `description` - What the agent does
- `protocols` - Supported protocols (hcs-10, a2a, mcp, etc.)
- `capabilities` - Agent capabilities (chat, search, etc.)
- `endpoint` - Connection endpoint URL
- `registry` - Source registry
- `topicId` - Hedera topic ID (for HCS agents)

## Notes

- UAID format: `protocol://identifier/name`
- Common protocols: hcs10, erc8004, a2a
- Returns 404 if agent not found
