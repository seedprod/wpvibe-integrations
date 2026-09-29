# WPVibe integrations

Official client configuration for [WPVibe](https://wpvibe.ai), by SeedProd. WPVibe connects AI assistants to your WordPress sites.

## What you can do

- Create and edit WordPress posts and pages.
- Manage media, WooCommerce, plugins, and site settings.
- Inspect site health and run supported WordPress operations without SSH.
- Edit themes in an isolated draft, preview changes, and publish after approval.

Sensitive operations use server-enforced approval gates and audit logging. WordPress permissions still apply.

## Requirements and authentication

1. Install and activate the free [WPVibe WordPress plugin](https://wordpress.org/plugins/vibe-ai/) on a site you administer.
2. Add the remote MCP endpoint `https://mcp.wpvibe.ai/mcp` to your AI client.
3. Complete WPVibe OAuth in your browser using your email verification code.
4. Ask your AI to connect your WordPress site and approve the connection in WordPress.

The endpoint supports Streamable HTTP, OAuth discovery, dynamic client registration, and PKCE. No shared API key or local server is required. The client must support remote MCP and OAuth.

All tools are available on the free plan, with a daily usage allowance. Paid plans increase that allowance. WPVibe usage is separate from your AI provider's limits. See [current pricing](https://mcp.wpvibe.ai/pricing).

## Cursor

This repository contains a `.cursor-plugin/plugin.json` manifest and `mcp.json` for plugin installation. Marketplace availability depends on review.

You can also add this configuration to Cursor's MCP settings:

```json
{"mcpServers":{"wpvibe":{"url":"https://mcp.wpvibe.ai/mcp"}}}
```

## Grok Build

This repository contains `.grok-plugin/plugin.json` and `.mcp.json`. Marketplace availability depends on review.

To connect directly:

```sh
grok mcp add --transport http wpvibe https://mcp.wpvibe.ai/mcp
```

## Gemini CLI

```sh
gemini extensions install https://github.com/seedprod/wpvibe-integrations
```

Complete OAuth when prompted. If authentication is pending, use `/mcp auth wpvibe` in Gemini CLI.

## Example prompts

- List my WordPress sites and check which plugins need updating.
- Create a draft blog post about our new service and leave it unpublished for review.
- Inspect my homepage and propose changes before editing a draft theme.

## Network access and privacy

The client connects to `https://mcp.wpvibe.ai/mcp` and its OAuth endpoints on `mcp.wpvibe.ai`. WPVibe relays authorized actions to WordPress sites that the user explicitly connects. WordPress connections use revocable Application Passwords. Never place credentials in these configuration files or commit them to Git.

This repository contains only client configuration, public branding, and documentation. It does not bundle the hosted service, install scripts, shell hooks, or credentials. The [WordPress plugin source](https://github.com/seedprod/vibe-ai) is maintained separately.

## Support

- [Documentation](https://wpvibe.ai/docs/)
- [Support](https://wpvibe.ai/support/)
- Email: support@wpvibe.ai

## License

The client configuration and documentation are MIT licensed. WPVibe names and logos remain the property of their respective owners; the license does not grant trademark rights. The hosted service is governed by the [WPVibe Terms of Service](https://wpvibe.ai/terms/) and [Privacy Policy](https://wpvibe.ai/privacy/).
