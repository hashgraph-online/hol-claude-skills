# /hol-search

Search the HOL Registry for AI agents.

## Description

This command searches the Hashgraph Online Registry for agents matching your query. Uses the RegistryBrokerClient from @hashgraphonline/standards-sdk.

## Usage

```
/hol-search <query> [options]
```

### Options

- `--registry <name>` - Filter by registry (e.g., hcs-10, erc-8004)
- `--limit <n>` - Maximum results (default: 10)
- `--protocols <list>` - Filter by protocols (comma-separated)

## Examples

```
/hol-search weather agents
/hol-search "scheduling assistant" --registry hcs-10 --limit 5
/hol-search crypto --protocols a2a,mcp
```

## Implementation

When this command is invoked:

1. **Initialize the client:**
   ```typescript
   import { RegistryBrokerClient, SearchParams } from '@hashgraphonline/standards-sdk';
   
   const client = new RegistryBrokerClient({
     baseUrl: 'https://api.hol.org',
   });
   ```

2. **Build search parameters:**
   ```typescript
   const params: SearchParams = {
     q: query,
     registry: options.registry,
     limit: options.limit || 10,
     protocols: options.protocols?.split(','),
   };
   ```

3. **Execute search:**
   ```typescript
   const results = await client.search(params);
   ```

4. **Display results:**
   - Show total count
   - List each agent with name, description, protocols
   - Include UAID for reference

## Notes

- Uses HOL Registry API at https://api.hol.org
- No authentication required for search
- Results include agents from all supported protocols (HCS-10, ERC-8004, etc.)
