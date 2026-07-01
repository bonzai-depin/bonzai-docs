# Connectors

Connectors let an agentic team work with the systems a business already uses.

## Current production connector actions

| System | Examples |
| --- | --- |
| Stripe | Checkout sessions, subscriptions, charges, refunds |
| HubSpot | Create/update contacts, create deals, advance deal stages |
| QuickBooks | Create/send invoices, record payments and bills |
| Sage Accounting | Create contacts and sales invoices, record payments |
| Slack | Post approved messages to channels |

## Connect safely

1. Open Company → Connectors.
2. Select the service.
3. Enter the requested credential/account identifier.
4. Test the connection.
5. Grant it only to teams and skills that need it.
6. Choose approval requirements for consequential actions.

Secrets are not placed in prompts. They are encrypted locally through operating-system protection when available and used by the desktop connector proxy.

## Demo vs production

Demo mode creates clearly labelled simulated results. Production mode calls the real service. If a production action has no executor, BonzAI fails clearly rather than reporting fake success.

## Removing access

Revoking a connector removes its stored credential and prevents new actions. It does not undo actions already completed in the third-party system.
