# How to connect LinkedIn to Claude Code, ChatGPT and any AI agent

**Yes, Claude, ChatGPT and other AI agents can work in your LinkedIn account.** LinkedIn has no official MCP server, and most of its API needs an approved developer app. Cotlet.dev connects your own signed-in LinkedIn to any AI agent, so the AI schedules posts, answers comments and messages, and invites leads when you ask in plain words.

## What you can ask

> Schedule my next 5 posts for Tuesday and Thursday at 9 am.

> Reply to the new comments on my last post. Show me the drafts first.

> Invite these 20 people from my lead list to connect, with a short note.

> Find heads of marketing at SaaS companies in Austin and list them.

> Which unread messages are from potential clients? Summarize them.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install linkedin-cotlet-mcp        # or run it once: uvx linkedin-cotlet-mcp connect
linkedin-cotlet-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 linkedin_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 linkedin_agent.py status    # is LinkedIn ready in your Cotlet.dev account
python3 linkedin_agent.py guide     # LinkedIn screens and sign-in link
python3 linkedin_agent.py read      # open LinkedIn, read the page, close the browser
python3 linkedin_agent.py tools     # list Cotlet.dev tools
```

## Questions from LinkedIn users

**Does LinkedIn have an MCP server?**

LinkedIn has no official MCP server. Open-source servers run on your own computer; Cotlet.dev is hosted, works 24/7 in your own LinkedIn and connects to Claude, ChatGPT, Cursor and any MCP client.

**How do I get a LinkedIn API key?**

LinkedIn gives API keys to a registered developer app, and most products need LinkedIn's approval. With Cotlet.dev you need no LinkedIn API key: you sign in to LinkedIn once and your agent works there.

**Is there an official ChatGPT or Claude app for LinkedIn?**

Yes, but not for this. ChatGPT has LinkedIn apps for profile lookup and read-only ads reporting, and Claude has LinkedIn Hiring Pro for posting one job (checked 6 Nov 2026). None of them posts for you, answers comments and messages or invites leads. Cotlet.dev does that in your own LinkedIn account.

**How do I connect LinkedIn to ChatGPT?**

Add Cotlet.dev as an app in ChatGPT (Settings → Apps, connector URL `https://cotlet.dev/mcp/v1`), sign in to LinkedIn once in your Cotlet.dev Cloud Browser, and ask ChatGPT in plain words. No code and no LinkedIn API key.

**Is there a way to use Claude with LinkedIn?**

Yes. In Claude Code run the one-line `claude mcp add` command above; in the Claude app add `https://cotlet.dev/mcp/v1` as a custom connector. Claude then works in your own LinkedIn account.

## Also works with

- [Medium MCP](https://github.com/cotlet-connect/medium-mcp)
- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/linkedin-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=linkedin

Start free: https://cotlet.dev/signup?app=linkedin&utm_source=github&utm_medium=readme&utm_campaign=linkedin
