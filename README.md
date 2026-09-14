<!-- mcp-name: tools.apricot/apricot -->

# Apricot MCP
![Logo Apricot](assets/apricot-logo.svg)

Public information page for the **Apricot** [Model Context Protocol](https://modelcontextprotocol.io)
(MCP) server — the remote MCP endpoint that lets AI coding agents (Claude Code, OpenCode, Codex,
and other MCP clients) manage [Apricot](https://apricot.tools) projects and SysML2 models directly
from a conversation.

This repository does not contain the server's implementation. It exists to give the MCP server a
public, citable home — a discoverable `repository` reference for registries such as the
[official MCP Registry](https://registry.modelcontextprotocol.io) and the
[GitHub MCP Registry](https://github.com/mcp) — while the implementation itself stays in
Apricot's private monorepo.

- **Live endpoint**: `https://mcp.apricot.tools/`
- **Product**: [apricot.tools](https://apricot.tools) — a SysML2 (Systems Modeling Language v2)
  editor with an in-editor AI assistant ("Alicia"), by [Metadev](https://metadev.pro).
- **Protocol version**: [2026-07-28](https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro)
- **Transport**: streamable HTTP, OAuth 2.1 (Authorization Code + PKCE, with Dynamic Client
  Registration) — no manual token to create or paste.

> **Note:** the registry namespace above (`tools.apricot/apricot`) reflects the intended naming,
> matching Structura's convention (reverse-DNS of the product domain). Confirm it against the
> actual `server.json` once Apricot MCP is first published to the MCP Registry.

## What it does

- List, load, create, or delete your Apricot projects.
- Browse and read the files of a project.

> Editing and validating a SysML2 model (set current model, delta edits, validation) is currently
> only available through Alicia, Apricot's in-editor assistant — those tools are scope-gated and
> not yet exposed to general MCP clients over this endpoint.

## Tools

The authoritative list is always what the live server reports over `tools/list`; the table below
is a convenience summary and may lag a version behind.

| Tool | What it does |
| --- | --- |
| `list_projects` | List the caller's Apricot projects. |
| `create_project` | Create a new project (starts with no files). |
| `load_project` | Load a project the caller owns, by id. |
| `update_project` | Update a project's name or description. |
| `delete_project` | Permanently delete a project the caller owns. |
| `list_project_files` | List a project's files (name/path/updatedAt, no content). |
| `get_project_file` | Read one file's full content from a project. |

## Install

Any MCP-capable agent can connect. A few examples:

### Claude Code

```bash
claude mcp add --transport http apricot https://mcp.apricot.tools/
```

Then run `/mcp` inside a Claude Code session, select **apricot**, and choose **Authenticate**.

### OpenCode

```bash
opencode mcp add
```

Pick **remote**, name it `apricot`, and paste `https://mcp.apricot.tools/`. Then:

```bash
opencode mcp auth apricot
```

### Codex

```bash
codex mcp add apricot --url https://mcp.apricot.tools/
codex mcp login apricot
```

Each of these opens a browser window with the normal Apricot login (Google/GitHub) — approve it
there, and the agent reuses that session from then on.

## Support

- Product and account questions: [apricot.tools](https://apricot.tools)
- Issues with the MCP server itself: open an issue on this repository.

## License

See [LICENSE](./LICENSE). This repository's own content (this README, the license file) is
provided for informational and discovery purposes; it does not grant any rights to the Apricot
service, product, or its non-public source code.

---

&copy; [Metadev](https://metadev.pro), 2026.
