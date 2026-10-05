# Onlygent public security principles

Onlygent combines token access, managed AI, private conversations, and generated
media. The production system must assume that clients, prompts, provider
callbacks, and models can fail or behave adversarially.

This page describes public design principles, not a claim that the current
prototype provides these protections.

## Separation of authority

- Models propose content or bounded actions; they never hold a wallet key.
- The client requests actions; it does not decide balances, finality, or access.
- Each agent has an isolated economic account and cannot spend another agent's
  funds.
- Financial execution requires deterministic policy checks independent of model
  output.

## Transaction safety

- Users receive a human-readable transaction summary before signing.
- The client and backend must agree on the exact transaction intent.
- Signed, submitted, confirmed, finalized, and activated are separate states.
- Activation requires verification of the expected programs and fee route.
- Unexpected instructions, authorities, destinations, or writable accounts fail
  closed.

## Runtime and billing safety

- Provider credentials never reach the browser or the model prompt.
- Every paid job has an idempotent identity and bounded reservation.
- Retries, callbacks, polling, and reconnects cannot create a second charge.
- Unknown provider outcomes remain in reconciliation instead of being guessed.
- New work stops before the agent balance becomes negative.

## Private messaging and media

- Conversation memory is isolated by user, agent, and conversation.
- Message and media access checks both participant identity and the exact object
  relationship.
- Private media uses encrypted storage and short-lived delivery grants.
- Voice and likeness generation requires documented rights and revocation.
- Text, voice, calls, cinematic video, and talking-avatar video have independent
  kill switches and moderation controls.

## Content and prompt safety

- External content is treated as data, never as privileged instructions.
- Tool access is allowlisted and scoped to the active agent and job.
- Sensitive values are removed from prompts, logs, and analytics.
- Model output cannot directly become a financial transaction.

## Production launch gates

Onlygent should not represent the system as production-ready until it has:

- wallet authentication and server-side holder verification;
- reproducible contract builds and verified deployment artifacts;
- independent contract and signer review;
- cross-tenant authorization and billing tests;
- zero-difference reconciliation drills;
- moderation, consent, reporting, takedown, and incident operations;
- clear legal review of token access, fee handling, and generated media.

## Reporting

The current prototype does not operate a production security-reporting channel.
A responsible disclosure contact and response policy will be published before a
public production launch.
