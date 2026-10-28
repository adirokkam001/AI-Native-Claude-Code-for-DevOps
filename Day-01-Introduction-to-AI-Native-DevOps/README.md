# Day 1 — Introduction to AI-Native DevOps with Claude Code

## Overview

Day 1 introduced AI-Native DevOps and demonstrated how Claude Code can assist engineers with project analysis, application development, Docker operations, testing, and troubleshooting.

The session included a RHEL 10 setup and a practical demonstration of building and testing a Dockerized application.

## Topics Covered

1. Introduction to AI-Native DevOps
2. Traditional DevOps vs. AI-Native DevOps
3. Claude Chat vs. Claude Code
4. Four principles for using AI agents
5. Claude Code setup on RHEL 10
6. Project context using CLAUDE.md
7. Dockerized application development
8. Application testing and health checks
9. AI-assisted troubleshooting
10. Git fundamentals and security practices

## Four Principles for Using AI Agents

### 1. Provide Clear Context
Explain the project, requirements, architecture, and constraints before asking the agent to work.

### 2. Maintain Project Instructions
Use CLAUDE.md to document project rules, commands, architecture, and requirements.

### 3. Review Permissions
Review file access and command execution requests. Never blindly approve risky operations.

### 4. Test and Verify
Review changes, inspect logs, run tests, and verify the final result while retaining human control.

## Practical Work

The trainer's overview covered a website served by HTTPD inside Docker, using host port 88 mapped to container port 80.

The detailed session notes also document a Flask application with `/` and `/health` endpoints, containerization, Git version control, and an intentionally introduced application failure that was investigated and fixed.

## Key Learnings

- AI agents can support multiple stages of the DevOps lifecycle.
- Claude Code can work with project files and run permitted commands.
- Docker helps package applications into containers.
- Logs and configuration files provide evidence for troubleshooting.
- AI-generated changes must be reviewed and tested.
- Security and human approval remain essential.

## Related Notes

- [AI-Native DevOps Concepts](concepts.md)
- [RHEL 10 Installation](installation-rhel10.md)
- [Docker Practical](docker-practical.md)
- [Troubleshooting](troubleshooting.md)

## Conclusion

Day 1 provided an introduction to AI-Native DevOps and the use of Claude Code for application development, containerization, testing, and troubleshooting.

Future sessions will expand these skills into additional DevOps tools and integrations.