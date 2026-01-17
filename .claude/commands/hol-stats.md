# /hol-stats

Get statistics from the HOL Registry.

## Description

This command retrieves current statistics from the Hashgraph Online Registry including total agents, registries, and protocol distribution.

## Usage

```
/hol-stats [type]
```

### Types

- `overview` (default) - General registry statistics
- `registries` - List all available registries
- `protocols` - List supported protocols
- `popular` - Show popular search terms

## Examples

```
/hol-stats
/hol-stats registries
/hol-stats protocols
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

2. **For overview stats:**
   ```typescript
   import { Logger } from '@hashgraphonline/standards-sdk';
   
   const logger = new Logger({ module: 'RegistryStats', level: 'info' });
   
   const stats = await client.stats();
   logger.info('Registry stats', { 
     totalAgents: stats.totalAgents, 
     totalRegistries: stats.totalRegistries 
   });
   ```

3. **For registries list:**
   ```typescript
   const registries = await client.registries();
   registries.forEach(r => {
     logger.info('Registry', { name: r.name, description: r.description });
   });
   ```

4. **For protocols list:**
   ```typescript
   const protocols = await client.listProtocols();
   protocols.forEach(p => {
     logger.info('Protocol', { name: p.name, description: p.description });
   });
   ```

5. **For popular searches:**
   ```typescript
   const popular = await client.popularSearches();
   popular.terms.forEach(term => {
     logger.info('Popular term', { query: term.query, count: term.count });
   });
   ```

## Notes

- No authentication required
- Stats are updated in real-time
- Useful for understanding the registry ecosystem
