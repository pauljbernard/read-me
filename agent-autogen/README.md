# Autogen Designer Configuration

## Purpose
A configuration template for [Project Name] built using **Autogen Designer**. This guide explains best practices for defining collaborative agents with Microsoft's Autogen framework. Replace `[Project Name]` throughout with your application's name.

## Features
- Visual designer for configuring agent roles and message routing
- Support for YAML or JSON configuration output
- Standard sections for goals, tools, and memory
- Parameters for environment-based settings and secrets
- Sample evaluation hooks for conversations
- Guidelines for integrating external APIs and services

## Getting Started
1. Install Autogen Designer and the Autogen runtime.
2. Create a new design in the tool and define agent roles, goals, and connections.
3. Export the configuration to `configs/`.
4. Invoke the Autogen runtime with this configuration to start your agent team.

## Configuration Guidelines
- Use clear names for each agent and specify responsibilities.
- Document prompts and tools in dedicated sections.
- Isolate secrets with environment variables or a secrets manager.
- Describe error handling and fallback logic.
- Include comments or metadata that explain the conversation flow.

## Directory Structure
```
agent-autogen/
├── configs/           # Autogen Designer configuration files
└── README.md          # This template
```

## Non-Functional Requirements
- Validate configuration files with available schema tools.
- Provide tests to ensure agent interactions behave as expected.
- Run configuration validation in CI before merging changes.

## Global Standards

### Security Standards
- Do not store API keys or credentials in configuration files.
- Limit edit permissions for Autogen designs to authorized team members.
- Mask sensitive data in logs or transcripts.

### Logging Specifications
- Define log levels for agent messages.
- Centralize logs for post-run analysis.

### Error Handling
- Provide default responses when agents encounter failures.
- Document retry and recovery strategies for external integrations.

## Customization Notes
- Extend the feature list with domain-specific capabilities.
- Update the directory structure as your project grows.
- Document how your runtime loads and starts this configuration.
