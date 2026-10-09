<p align="center"><img src="icon.png" width="96" height="96" alt="HellouOne"></p>

# HellouOne MCP server

Work with your HellouOne customer conversations, contacts, inboxes, agents and reports from your AI assistant.

[HellouOne](https://hellou.ai) is an omnichannel customer engagement platform (WhatsApp, web chat, email, social, voice). Its remote MCP server lets your assistant:

- read and search conversations and contacts;
- list inboxes, teams, agents and labels;
- pull conversation, agent and team reports;
- when an administrator allows it, make changes such as creating labels or canned responses.

Reads are marked read-only. Tools that change data are marked as destructive, so your assistant asks before running them, and every change is recorded in the account's audit log.

- **Server:** `https://mcp.hellou.ai/mcp` (Streamable HTTP). One URL serves every account; the credential decides which account.
- **Docs:** https://one.hellou.ai/docs/mcp.html ([español](https://one.hellou.ai/docs/es/mcp.html))

## Cursor

Install it from the Cursor Marketplace or [cursor.directory](https://cursor.directory/plugins/hellouone), or add the server yourself to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "hellouone": { "url": "https://mcp.hellou.ai/mcp" }
  }
}
```

On first use Cursor opens HellouOne's sign-in page in your browser. An administrator picks the account and decides whether the assistant may make changes, then Cursor takes the connection back. There's no token to create or paste. Disconnect it any time in **Settings → Integrations → AI clients (MCP)**.

Prefer a personal token (for example on a machine without a browser)? Create one on that same settings page and add `"headers": { "Authorization": "Bearer ${env:HELLOUONE_MCP_TOKEN}" }` to the entry above, with the token exported as `HELLOUONE_MCP_TOKEN`. Keep it out of chat, logs and committed files.

## Other clients

- **claude.ai and ChatGPT:** add `https://mcp.hellou.ai/mcp` as a custom connector. You sign in with OAuth on HellouOne's consent page, where an administrator picks the account and decides whether the assistant may make changes. You don't paste a token.
- **Claude Code:**

  ```bash
  claude mcp add --transport http hellouone https://mcp.hellou.ai/mcp \
    --header "Authorization: Bearer hcm_..."
  ```

## Español

HellouOne es una plataforma omnicanal de atención al cliente (WhatsApp, chat web, correo, redes sociales, voz). Su servidor MCP remoto permite que tu asistente:

- lea y busque conversaciones y contactos;
- liste bandejas, equipos, agentes y etiquetas;
- consulte reportes de conversaciones, agentes y equipos;
- si un administrador lo permite, haga cambios como crear etiquetas o respuestas rápidas.

**En Cursor:** instálalo desde el Marketplace de Cursor o agrega el servidor solo con su URL (configuración de arriba). La primera vez, Cursor abre la página de inicio de sesión de HellouOne y no necesitas token. **En claude.ai y ChatGPT:** agrega `https://mcp.hellou.ai/mcp` como conector personalizado e inicia sesión. Un administrador elige la cuenta y decide si el asistente puede hacer cambios. Cada cambio queda en el registro de auditoría de la cuenta.

Documentación: https://one.hellou.ai/docs/es/mcp.html

## Links

- Privacy: https://hellou.ai/en/legal/privacy/
- Terms: https://hellou.ai/en/legal/terms/
- MCP Registry: `ai.hellou/hellouone`
