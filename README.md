# Docker CAgent + GitHub MCP Integration

## Overview

This project demonstrates how to integrate Docker CAgent with the GitHub MCP Server to create an AI-powered GitHub assistant.

The assistant can:

- Connect with GitHub repositories
- Search GitHub issues
- Create issues
- Update issues
- Add comments to issues
- Use natural language commands

---

# Problem Statement

Managing GitHub repositories manually becomes repetitive when handling:

- Issue tracking
- Bug reporting
- Issue updates
- Repository management

The goal of this project was to:

1. Configure Docker CAgent
2. Integrate GitHub MCP
3. Use AI for GitHub automation
4. Build a reusable DevOps assistant

---

# Challenges Faced

## YAML Parsing Errors

Error:

string was used where mapping is expected

### Cause

- Incorrect YAML formatting
- PowerShell encoding issues
- UTF BOM characters

### Solution

- Used PowerShell here-strings
- Saved files using ASCII encoding
- Avoided malformed echo commands

---

## PowerShell Encoding Problems

Windows PowerShell 5.x does not support utf8NoBOM.

### Solution

Used:

Out-File -Encoding ascii

---

## GitHub MCP Authentication Issues

Initially the MCP server could not access GitHub APIs.

### Solution

Used:

GITHUB_PERSONAL_ACCESS_TOKEN=${GITHUB_TOKEN}

to correctly pass the token into the MCP container.

---

# Technologies Used

- Docker Desktop
- Docker CAgent
- GitHub MCP Server
- Google Gemini API
- PowerShell
- Git
- YAML

---

# Project Structure

.
??? agent.yaml
??? agent1.yaml
??? README.md
??? MCP/

---

# Running the Project

## Pull Docker Agent

docker pull docker/cagent

---

## Run the Agent

docker run -it --rm `
-v ${PWD}:/workspace `
-w /workspace `
-e GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY" `
-e GITHUB_TOKEN="YOUR_GITHUB_TOKEN" `
docker/cagent run agent1.yaml

---

# Example Commands

Use get_me tool

List issues in owner/repository

Create issue in owner/repository

Search issues labeled bug

---

# Learning Outcomes

- Learned Docker AI agent orchestration
- Understood MCP architecture
- Solved YAML parsing issues
- Fixed PowerShell encoding problems
- Integrated GitHub APIs with AI agents

---

# Security Notes

- Never expose API keys
- Never commit GitHub tokens
- Use .gitignore
- Rotate exposed tokens immediately

---

# Author

Built as a hands-on learning project for exploring:

- Docker AI Agents
- MCP integrations
- GitHub automation
- AI-assisted DevOps workflows
