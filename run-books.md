# Principles

The proposed solution is intended to meet the following principles:
- Instructions should come to the responder with the alert; the responder does not have to go looking for the run-book.
- Instructions bias towards clearly actionable steps; responders do not need to understand deep context before acting.
- Where immediate mitigations fail and deeper analysis is needed, that is supported with documentation.
- It should be easy to enlist the help of an LLM in the case of deeper problem solving.

# Proposed Solution

Split the run-book into two parts with clear and distinct purposes.

## Initial Response
**Purpose**: Allow the responder to act fast, trying likely mitigations and remediations with minimal delay.  Takes the form of clear easy-to-follow instructions.  Bias towards action over understanding in depth.

- Document lives in the Datadog monitor's description, which is passed to the responder with the alert.
- Includes the following information as standard:
   - A brief explanation of what the alert means and why the monitor was created.
   - A brief list of likely causes.
   - A list of actionable steps alongside instructions for how to check if they've worked.
   - A link to the second part of the runbook.

## Problem Solving
**Purpose**: Facilitate deeper problem solving in the case that the initial response failed to address the incident.  Takes the form of longer documentation.  Explains the service, its architecture, dependencies, and implementation.  Bias towards deep understanding to allow problem solving over actions.  Provides context for an LLM acting in support of the responder.

- Document(s) take the form of markdown documents in the failing component's repository.
- Information MAY be spread across multiple markdown files, e.g. README.md, OPERATIONS.md, and any other that make sense.
- Repo should include an AGENTS.md file as an entry point.
   - AGENTS.md file should include a section entitled `Incident Response` as an entry point, with directions to other resources where appropriate.
