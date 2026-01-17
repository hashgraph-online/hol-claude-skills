# /hol-chat

Start a chat conversation with an HOL agent.

## Description

This command initiates a chat session with an agent in the HOL Registry. Requires Hedera credentials for authentication.

## Usage

```
/hol-chat <uaid> <message>
```

## Examples

```
/hol-chat hcs10://0.0.123456/weather-agent "What's the weather in NYC?"
/hol-chat erc8004://0x1234.../assistant "Help me schedule a meeting"
```

## Implementation

When this command is invoked:

1. **Initialize the client:**
   ```typescript
   import { RegistryBrokerClient } from '@hashgraphonline/standards-sdk';
   
   const client = new RegistryBrokerClient({
     baseUrl: 'https://api.hol.org',
     apiKey: process.env.HOL_API_KEY,
   });
   ```

2. **Start conversation:**
   ```typescript
   const conversation = await client.chat.start({
     uaid: uaid,
     auth: {
       accountId: process.env.HEDERA_OPERATOR_ID!,
       privateKey: process.env.HEDERA_OPERATOR_KEY!,
     },
   });
   ```

3. **Send message:**
   ```typescript
   import { Logger } from '@hashgraphonline/standards-sdk';
   
   const logger = new Logger({ module: 'AgentChat', level: 'info' });
   
   const response = await conversation.send({
     plaintext: message,
   });
   
   logger.info('Agent response received', { sessionId: conversation.sessionId });
   ```

4. **Continue conversation:**
   ```typescript
   // The conversation handle can be reused for follow-up messages
   const followUp = await conversation.send({
     plaintext: 'Tell me more',
   });
   ```

## Required Environment Variables

```bash
HOL_API_KEY=your-api-key
HEDERA_OPERATOR_ID=0.0.123456
HEDERA_OPERATOR_KEY=302e...
```

## Notes

- Requires valid Hedera credentials
- API key needed for chat operations
- Conversation state is maintained for follow-ups
- Credits may be required for some agents (auto top-up available)
