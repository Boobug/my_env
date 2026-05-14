# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository manages GRC (Governance, Risk, and Compliance) tooling. It is the central workspace for automating, integrating, and maintaining tools related to:

- **Governance**: Policy management, access controls, audit trails
- **Risk**: Risk registers, threat modeling, risk scoring, vulnerability tracking
- **Compliance**: Regulatory framework mapping (SOC 2, ISO 27001, NIST CSF, GDPR, HIPAA, PCI-DSS), evidence collection, control testing

## Repository Setup

This repo is in its initial state. As tools and scripts are added, update this file with:

- Build/install commands
- How to run linters and tests (including single-test invocation)
- Environment variable requirements and how to configure them (e.g., via `.env.example`)
- Any external service dependencies (e.g., JIRA, ServiceNow, Drata, Vanta, Wiz, Qualys)

## Architecture Conventions (to be followed as code is added)

- **Tool scripts** should live under `tools/` with one subdirectory per domain (e.g., `tools/risk/`, `tools/compliance/`, `tools/audit/`)
- **Integrations** with third-party GRC platforms belong under `integrations/`
- **Shared utilities** (auth helpers, API clients, data models) belong under `lib/` or `src/shared/`
- **Configuration and framework mappings** (e.g., control-to-requirement matrices) belong under `config/`
- **Reports and templates** belong under `templates/`

## GRC Domain Notes

- Control IDs should follow a consistent naming scheme (e.g., `CC6.1` for SOC 2, `A.9.1.1` for ISO 27001) — do not invent new IDs; use the official framework identifiers.
- Risk scores should use a defined methodology (likelihood × impact). Document the scoring matrix in `config/risk-matrix.md` once established.
- Evidence artifacts tied to compliance controls must reference a control ID in their metadata or filename.
- Automation that modifies policy documents or risk register entries should always produce a diff/audit log before writing changes.
