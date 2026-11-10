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

## Run it locally (stdio)

This repo is a real MCP server. It speaks MCP over stdio, lists its LinkedIn tools without any key, and forwards every tool call to the hosted Cotlet.dev server. The hosted URL above stays the recommended way. Use this when your client only starts local servers.

```json
{"mcpServers":{"linkedin":{"command":"uvx","args":["linkedin-cotlet-mcp"],"env":{"COTLET_API_KEY":"your-key"}}}}
```

Or with Docker:

```bash
docker build -t linkedin-mcp .
docker run -i --rm -e COTLET_API_KEY linkedin-mcp
```

Tools: `linkedin_guide`, `linkedin_status`, `linkedin_open`, `linkedin_read`, `linkedin_click`, `linkedin_type`, `linkedin_close`. Without `COTLET_API_KEY` a tool call answers: "Set COTLET_API_KEY. Get a key at https://cotlet.dev/app".

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
python3 linkedin_agent.py serve     # start the stdio MCP server (same as no argument)
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

## Find it on

- [LinkedIn on Cotlet.dev](https://cotlet.dev/integrations/linkedin-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=linkedin&utm_content=find)
- [PyPI package linkedin-cotlet-mcp](https://pypi.org/project/linkedin-cotlet-mcp/)
- [Glama](https://glama.ai/mcp/servers/cotlet-connect/linkedin-mcp)
- [LobeHub](https://lobehub.com/mcp/cotlet-connect-linkedin-mcp)
- [Step-by-step guide (PDF) on Internet Archive](https://archive.org/details/cotlet-connect-linkedin-to-ai-agents-guide)

## Also works with

- [Medium MCP](https://github.com/cotlet-connect/medium-mcp)
- [Mangomint MCP](https://github.com/cotlet-connect/mangomint-mcp)
- [Wanderlog MCP](https://github.com/cotlet-connect/wanderlog-mcp)
- [SmugMug MCP](https://github.com/cotlet-connect/smugmug-mcp)
- [Garmin Connect MCP](https://github.com/cotlet-connect/garmin-mcp)
- [Housecall Pro MCP](https://github.com/cotlet-connect/housecall-pro-mcp)
- [Crexi MCP](https://github.com/cotlet-connect/crexi-mcp)
- [DistroKid MCP](https://github.com/cotlet-connect/distrokid-mcp)
- [EstimateOne MCP](https://github.com/cotlet-connect/estimateone-mcp)
- [Google Search Console MCP](https://github.com/cotlet-connect/google-search-console-mcp)
- [Lichess MCP](https://github.com/cotlet-connect/lichess-mcp)
- [Strava MCP](https://github.com/cotlet-connect/strava-mcp)
- [StreamElements MCP](https://github.com/cotlet-connect/streamelements-mcp)
- [Meetup MCP](https://github.com/cotlet-connect/meetup-mcp)
- [AccuRanker MCP](https://github.com/cotlet-connect/accuranker-mcp)
- [GetYourGuide MCP](https://github.com/cotlet-connect/getyourguide-mcp)
- [Idealista MCP](https://github.com/cotlet-connect/idealista-mcp)
- [Riverside MCP](https://github.com/cotlet-connect/riverside-mcp)
- [Udemy MCP](https://github.com/cotlet-connect/udemy-mcp)
- [Faire MCP](https://github.com/cotlet-connect/faire-mcp)
- [Buildertrend MCP](https://github.com/cotlet-connect/buildertrend-mcp)
- [Fresha MCP](https://github.com/cotlet-connect/fresha-mcp)
- [Booksy MCP](https://github.com/cotlet-connect/booksy-mcp)
- [BookingKoala MCP](https://github.com/cotlet-connect/bookingkoala-mcp)
- [Milanote MCP](https://github.com/cotlet-connect/milanote-mcp)
- [Partiful MCP](https://github.com/cotlet-connect/partiful-mcp)
- [Contractor Foreman MCP](https://github.com/cotlet-connect/contractor-foreman-mcp)
- [Pixieset MCP](https://github.com/cotlet-connect/pixieset-mcp)
- [GlossGenius MCP](https://github.com/cotlet-connect/glossgenius-mcp)
- [ZenMaid MCP](https://github.com/cotlet-connect/zenmaid-mcp)
- [FieldEdge MCP](https://github.com/cotlet-connect/fieldedge-mcp)
- [Phorest MCP](https://github.com/cotlet-connect/phorest-mcp)
- [DINGG MCP](https://github.com/cotlet-connect/dingg-mcp)
- [Invoice Simple MCP](https://github.com/cotlet-connect/invoice-simple-mcp)
- [PhotoShelter MCP](https://github.com/cotlet-connect/photoshelter-mcp)
- [RazorSync MCP](https://github.com/cotlet-connect/razorsync-mcp)
- [ShootProof MCP](https://github.com/cotlet-connect/shootproof-mcp)
- [Invoice2go MCP](https://github.com/cotlet-connect/invoice2go-mcp)
- [Appointy MCP](https://github.com/cotlet-connect/appointy-mcp)
- [Contractor+ MCP](https://github.com/cotlet-connect/contractor-plus-mcp)
- [Teachers Pay Teachers MCP](https://github.com/cotlet-connect/teachers-pay-teachers-mcp)
- [Bloom MCP](https://github.com/cotlet-connect/bloom-mcp)
- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/linkedin-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=linkedin

Start free: https://cotlet.dev/signup?app=linkedin&utm_source=github&utm_medium=readme&utm_campaign=linkedin
