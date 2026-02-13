# Releasing Under Feature Switches

## Context

Zilch uses LaunchDarkly feature switches as part of its release process. The core principle is the separation of **deployment** from **release**:

- **Deployment** is the act of putting code into an environment. It is managed through build pipelines and Argo, and is covered separately.
- **Release** is the act of making new or changed functionality available to users.

By deploying code behind a feature switch that is initially turned off, we can deploy at any time without affecting users. The switch is then enabled deliberately when the feature is ready for release. This gives us:

- **Incremental delivery** — features can be deployed before they are complete and released when ready.
- **Controlled release** — rollout can be staged and monitored.
- **Fast rollback** — a switch can be turned off without redeployment if problems arise.

This document covers the lifecycle of a feature-switch-controlled release: deciding when a switch is needed, creating it, deploying behind it, enabling it, and cleaning it up afterwards.

## When a Feature Switch Is Required

A feature switch is required for:

- **New features** — any new user-facing functionality.
- **Changes to existing behaviour** — modifications to how existing features work.

A feature switch is **not** normally required for:

- **Bug fixes** — defect corrections are typically released directly.

There will be grey areas. Where there is doubt — for example, a refactor that carries significant regression risk — use judgement and discuss with the team.

## Creating a Flag

### Requesting a Flag

Flag creation is restricted to authorised maintainers. To request a new flag:

1. Create a Jira ticket (type `Task`) for the flag's **removal**. Parent it under the epic delivering the feature — the epic should not be closed until the flag has been cleaned up.
2. Specify the exact `key` for the flag in the ticket description.
3. Send a link to the Jira ticket to a maintainer, together with a description for the flag.

The maintainer will:

1. Verify that the flag key follows the naming conventions below.
2. Create the flag in LaunchDarkly using the key and description provided.
3. Add a link to the removal Jira ticket as a custom property on the flag.

If no maintainers are available within the team, someone outside the team may create the flag. In this case, the requestor is responsible for ensuring the removal ticket exists.

### Maintainers

The following people currently have the LaunchDarkly privileges required to create and maintain flags for the Merchant team:

- Nicklas Chapman

### Key Naming Conventions

Flag keys must follow these conventions:

1. **Be concise but meaningful.** It should be unambiguous what feature the flag controls, but avoid being overly descriptive. Three or four words is usually sufficient.
2. **Use consistent prefixes for sub-features.** If a feature has multiple capabilities that can be toggled independently, give them all the same prefix so they group in an alphabetical list.
3. **Use kebab-case.** Keys should be in lower case with dashes as separators, `just-like-this`.
4. **Avoid redundant terms.** The inclusion of `-enabled` is unnecessary and prohibited by these conventions.

## Deploying Behind a Flag

Once the flag has been created, code is developed and deployed with the flag turned off. The detail of the deployment process is out of scope for this document, but the key point is that deployment should not change user-facing behaviour — the flag remains off until the feature is deliberately released.

## Enabling a Flag

_This section will be expanded with a detailed enablement playbook covering staged rollout, regression testing, and monitoring expectations. For now, coordinate flag enablement with the team and a maintainer._

## Removing a Flag

Every active flag should be paired with a Jira ticket for its removal. Once a feature is fully released and stable:

1. Confirm the flag is fully rolled out and has been stable for an appropriate period.
2. Remove all code references to the flag.
3. Archive or delete the flag in LaunchDarkly.
4. Close the removal Jira ticket.
