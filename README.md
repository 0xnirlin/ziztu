# Ziztu MCP server and skills

[Ziztu](https://getziztu.com) is an AI video studio for micro dramas, anime episodes, viral reels, YouTube Shorts, TikTok videos and long faceless YouTube videos. This repository holds the public pieces an agent needs to use it:

- **The Ziztu MCP server**, hosted at `https://getziztu.com/mcp`. Connect it and your agent can create a project, ask the Director to plan an episode, price every shot in credits, and make first frames, clips, music and the final film, with the same characters in every shot.
- **Ziztu Planner**, a smaller server at `https://getziztu.com/mcp/planner` that plans episodes, writes scripts, loglines and shot lists, and prices each step. It makes no images or video.
- **Four skills** (MIT): `ziztu-viral-reels` writes viral faceless reels, YouTube Shorts and TikToks, `ziztu-faceless-youtube` plans and scripts faceless YouTube videos, `ziztu-micro-drama` writes binge-worthy vertical micro drama series and hands them to Ziztu, and `ziztu-cinematic-depth` stages AI images and video in depth so frames stop looking flat.
- **A portable Agent Plugin** ([`plugin.json`](plugin.json) and [`mcp.json`](mcp.json)) that bundles the MCP server and the skills for Hermes and other clients that read the Agent Plugins format.

Full docs: [getziztu.com/docs/mcp](https://getziztu.com/docs/mcp)

## Connect the MCP server

Both servers use OAuth. Add the address, sign in to Ziztu when the client asks, and approve the screen that opens. No install and no key.

| Client | How to add it |
| --- | --- |
| Claude (claude.ai, Desktop, mobile) | Customize, Connectors, Add custom connector, paste `https://getziztu.com/mcp`, then Connect. |
| Claude Code | `claude mcp add --transport http ziztu https://getziztu.com/mcp`, then `/mcp` to sign in. |
| Cursor | Copy [`.cursor/mcp.json`](.cursor/mcp.json) into your project's `.cursor/mcp.json`, then sign in when Cursor asks. |
| Hermes Agent | `hermes plugins install 0xnirlin/ziztu`, then `hermes plugins enable ziztu`, and sign in when Hermes asks. |
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
- Any agent that supports skills.sh: `npx skills add 0xnirlin/ziztu`.

`ziztu-viral-reels` picks a proven reel format, writes a 1 second hook and a Paradox, Escalation, Pivot, Payoff script, and builds the shot list for a faceless reel, YouTube Short or TikTok. Then it makes the reel in [Reel Factory](https://getziztu.com/reel-factory), the AI reel maker: one topic in, one vertical MP4 out with a voice, word captions and music.

`ziztu-faceless-youtube` picks a niche, studies how a working video is built without copying it, and writes a chapter by chapter script, titles and thumbnail ideas for a faceless YouTube channel. Then it makes the film in the [AI YouTube Video Maker](https://getziztu.com/ai-youtube-video-maker): a narrated video of 2 to 60 minutes in one look.

`ziztu-micro-drama` writes pitches, series bibles, season grids and Fountain episode scripts with a hook and a cliffhanger in every episode. Writing needs no Ziztu account. With the MCP server connected it imports each episode, plans the shots and shows the price before anything is made.

`ziztu-cinematic-depth` writes a soft foreground, a sharp subject and a hazy background into image and video prompts for models such as Seedance, Kling, Veo, Nano Banana and GPT Image, and fixes frames that look flat or pasted in.

## Make viral reels, Shorts and TikToks

- [AI reel maker for faceless reels](https://getziztu.com/reel-factory): 256 styles across 19 formats, or copy the style of your own reel.
- Reel styles: [diorama video maker](https://getziztu.com/reel-factory/diorama), [claymation video maker](https://getziztu.com/reel-factory/claymation), [animal facts videos](https://getziztu.com/reel-factory/animal-facts), [would you rather videos](https://getziztu.com/reel-factory/would-you-rather), [how deep is the ocean videos](https://getziztu.com/reel-factory/how-deep-is-the-ocean), [Zack D Films style videos](https://getziztu.com/reel-factory/zack-d-films-style), [stickman animation maker](https://getziztu.com/reel-factory/stickman-animation), [Minecraft style animation](https://getziztu.com/reel-factory/minecraft-animation) and [2.5D animation](https://getziztu.com/reel-factory/2-5d-animation).
- [Faceless video generator](https://getziztu.com/tools/faceless-video-generator), [AI YouTube Shorts generator](https://getziztu.com/tools/ai-youtube-shorts-generator), [AI TikTok video generator](https://getziztu.com/tools/ai-tiktok-video-generator) and [AI shorts generator](https://getziztu.com/tools/ai-shorts-generator).
- [Video hook generator](https://getziztu.com/tools/video-hook-generator), [TikTok script generator](https://getziztu.com/tools/tiktok-script-generator) and [reel caption generator](https://getziztu.com/tools/reel-caption-generator).
- Guides: [best AI reel makers](https://getziztu.com/blog/best-ai-reel-makers) and [how to make faceless reels with AI](https://getziztu.com/blog/how-to-make-faceless-reels-with-ai).

## Make faceless YouTube videos

- [AI YouTube video maker](https://getziztu.com/ai-youtube-video-maker): a YouTube link or an idea becomes a narrated film of 2 to 60 minutes, with titles, thumbnails, chapters and captions.
- [AI Instagram video maker](https://getziztu.com/ai-instagram-video-maker) for longer Instagram videos.
- Guides: [how to start a faceless YouTube channel](https://getziztu.com/blog/how-to-start-a-faceless-youtube-channel), [top faceless YouTube channels](https://getziztu.com/blog/top-faceless-youtube-channels) and [best AI YouTube video makers](https://getziztu.com/blog/best-ai-youtube-video-makers).

## More Ziztu tools

- [AI video generator](https://getziztu.com/tools/ai-video-generator) with Seedance, Kling, Hailuo and more on one credit balance.
- [OC maker](https://getziztu.com/oc-maker) for original characters.
- [Instagram video downloader](https://getziztu.com/tools/instagram-video-downloader).

## Registry

- Official MCP Registry: `com.getziztu/ziztu` and `com.getziztu/ziztu-planner` ([server.json](server.json))
- Glama: [Ziztu](https://glama.ai/mcp/connectors/com.getziztu/ziztu) and [Ziztu Planner](https://glama.ai/mcp/connectors/com.getziztu/ziztu-planner)

## Links

- Website: [getziztu.com](https://getziztu.com)
- Docs: [getziztu.com/docs](https://getziztu.com/docs)
- Privacy: [getziztu.com/privacy](https://getziztu.com/privacy)
- Support: support@getziztu.com

The skills are MIT licensed (see [LICENSE](LICENSE)). The Ziztu service is governed by its [terms](https://getziztu.com/terms).
