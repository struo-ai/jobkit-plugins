---
name: jobkit
description: Find Jobkit jobs, inquiries, customers and quotes, or create customer and work records and plan visits using the connected Jobkit MCP tools. Use only when the user asks to work with Jobkit.
---

Use the connected Jobkit tools and follow the instructions the Jobkit server
sends with the connection: they are the source of truth for how to read, write
and schedule. The tool schemas are the source of truth for what exists.

Start with `get_connection` to learn the authorized company and permissions. If
the company is wrong, have the user reconnect and choose the intended one. If
the connection needs authentication, use the client's sign-in flow. Never ask
for passwords, API keys or access tokens in conversation.

Confirm with the user before any tool that creates or changes a record. Report
only what the tools confirmed, and after a failed or uncertain write say the
outcome needs checking.
