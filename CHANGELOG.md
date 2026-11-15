# Changelog

## [0.2.0] - 2026-11-14

### Security
- Dependencies updated to clear 77 Dependabot alerts. `@modelcontextprotocol/sdk` moves from 0.5 to 1.32 and `zod` from 3 to 4; the unused packages `ai`, `inquirer`, `archiver` and `zod-to-json-schema` are removed.
- `fetch-chunk` and `ask-qwen` reject cache keys that are not 8 hex characters, so a crafted key can no longer read or delete files outside the chunk cache (CWE-22).

### Changed
- Node.js 18 or newer is required (was 16). The MCP SDK 1.x needs it.
- The server reports version 0.2.0 to MCP clients.

## [0.1.0]
- Initial release
- Basic functionality merged from gemini-mcp-tool
