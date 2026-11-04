# Ziztu MCP server and skills

[Ziztu](https://getziztu.com) is an AI video studio for micro dramas, anime episodes, reels and long YouTube videos. This repository holds the public pieces an agent needs to use it:

- **The Ziztu MCP server**, hosted at `https://getziztu.com/mcp`. Connect it and your agent can create a project, ask the Director to plan an episode, price every shot in credits, and make first frames, clips, music and the final film, with the same characters in every shot.
- **Ziztu Planner**, a smaller server at `https://getziztu.com/mcp/planner` that plans episodes, writes scripts, loglines and shot lists, and prices each step. It makes no images or video.
- **Two skills** (MIT): `ziztu-micro-drama` writes binge-worthy vertical micro drama series and hands them to Ziztu, and `ziztu-cinematic-depth` stages AI images and video in depth so frames stop looking flat.

Full docs: [getziztu.com/docs/mcp](https://getziztu.com/docs/mcp)

## Connect the MCP server

Both servers use OAuth. Add the address, sign in to Ziztu when the client asks, and approve the screen that opens. No install and no key.

| Client | How to add it |
| --- | --- |
| Claude (claude.ai, Desktop, mobile) | Customize, Connectors, Add custom connector, paste `https://getziztu.com/mcp`, then Connect. |
| Claude Code | `claude mcp add --transport http ziztu https://getziztu.com/mcp`, then `/mcp` to sign in. |
| Cursor | Copy [`mcp.json`](mcp.json) into `.cursor/mcp.json`, then sign in when Cursor asks. |
| Codex | `codex mcp add ziztu --url https://getziztu.com/mcp` |
| ChatGPT | Add a custom MCP server in the apps settings (developer mode) and choose OAuth. |
| Grok | grok.com/connectors, New Connector, Custom, paste the address. |

For scripts and unattended agents, Ziztu also has API keys (Studio, Settings, API keys); the docs show how to use them.

## What it costs

Ziztu works on credits. Every paid step shows its price in credits before it runs, the agent can ask for a dry run first, and a step that fails is refunded. Only the steps that write or make something are charged. Plans and credits are bought on [getziztu.com/pricing](https://getziztu.com/pricing), never inside the agent.

## Install the skills

The skills live in [`skills/`](skills). Each folder has a `SKILL.md`.

- Claude Code: install this repository as a plugin (it bundles both skills and the MCP server), or copy a skill folder into `~/.claude/skills/`.
- Codex and other agents that read skills: copy a skill folder into your agent's skills directory.

`ziztu-micro-drama` writes pitches, series bibles, season grids and Fountain episode scripts with a hook and a cliffhanger in every episode. Writing needs no Ziztu account. With the MCP server connected it imports each episode, plans the shots and shows the price before anything is made.

`ziztu-cinematic-depth` writes a soft foreground, a sharp subject and a hazy background into image and video prompts for models such as Seedance, Kling, Veo, Nano Banana and GPT Image, and fixes frames that look flat or pasted in.

## Registry

- Official MCP Registry: `com.getziztu/ziztu` and `com.getziztu/ziztu-planner` ([server.json](server.json))
- Glama: [Ziztu](https://glama.ai/mcp/connectors/com.getziztu/ziztu) and [Ziztu Planner](https://glama.ai/mcp/connectors/com.getziztu/ziztu-planner)

## Links

- Website: [getziztu.com](https://getziztu.com)
- Docs: [getziztu.com/docs](https://getziztu.com/docs)
- Privacy: [getziztu.com/privacy](https://getziztu.com/privacy)
- Support: support@getziztu.com

The skills are MIT licensed (see [LICENSE](LICENSE)). The Ziztu service is governed by its [terms](https://getziztu.com/terms).
