# Ephemeral Environments

## Also Known As
* Zephyrs (technically the term for an ephemeral environment instance - a play on a portmanteau of Zilch and Ephemeral)
* ZOE (technically the name of the orchestration service; stands for Zephyr Orchestration Engine)

## Context

A strategic DevOps project to build a platform for creating, managing, and destroying ephemeral environments — full, working, sandboxed stacks that engineers can use for development and debugging, and that pipelines can use for automated testing. Key benefits: no environment contention, clean state, and no wasted resource usage from long-running environments that exist even when unused.

### Key Terms

- **Zephyr** — an instance of an ephemeral environment (portmanteau of "Zilch" and "Ephemeral").
- **ZOE (Zephyr Orchestration Engine)** — the persistent platform that manages and orchestrates Zephyrs, accessed primarily via an API. Built by Piotr; had quality and process issues due to being developed largely in isolation without iterative peer review.
- **Zephyr Zero** — the first Zephyr build. Unlike a normal ephemeral, it is left running persistently. The intent is for each software engineering team to test and debug their own services in the environment so that confidence can be gained that the build is sound.

## Personnel

- Phil Stephenson (DevOps)
- Piotr Niebylski (DevOps)

## Running Notes

### 2026-02-18

Checked in with Nikos on Zephyr Zero testing progress. Two blockers being worked on:
- The VGS issue (known since 6 Feb; fix still pending).
- Work on the test lambda (used for test state management via direct DB SQL queries) — needed so test users can act as customers signing up on the environments.

Radek Kachel is working on the lambda.

### 2026-02-06

- ZOE MVP ready pending review by team.
- VGS routes not working; investigation concluded, actual fix pending.

### 2026-02-04

Project log created.
