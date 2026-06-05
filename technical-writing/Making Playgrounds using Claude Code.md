---
title: "Making Playgrounds using Claude Code"
source: "https://x.com/trq212/status/2017024445244924382"
author:
  - "[[@trq212]]"
published: 2026-01-30
created: 2026-05-20
description: "We've published a new Claude Code plugin called playground that helps Claude generate HTML playgrounds. These are standalone HTML files that..."
tags:
  - "clippings"
---
![画像](https://pbs.twimg.com/media/G_2-teGbUAMtRec?format=jpg&name=large)

We've published a new Claude Code plugin called **playground** that helps Claude generate HTML playgrounds. These are standalone HTML files that let you visualize a problem with Claude, interact with it and give you an output prompt to paste back into Claude Code.

I've found this can be really good interacting with the model in ways that are not well suited for text, for example to:

- Visualize the architecture of the codebase
- Adjust the design of a component
- Brainstorm layouting and design
- Tweak the balance of a game

To get started, install the plugin in Claude code by running the following commands: **/plugin marketplace update claude-plugins-official /plugin install playground@claude-plugins-official** Here are some of my favorite playgrounds I've made: **Changing the design of the AskUserQuestion Tool in Claude Code** prompt: "Use the playground skill to create an playground that helps me explore new layout changes to the AskUserQuestion Tool"

<video preload="none" tabindex="-1" playsinline="" aria-label="埋め込み動画" poster="https://pbs.twimg.com/amplify_video_thumb/2016958749647523843/img/JiDZx01_Kh206Dj-.jpg" style="width: 100%; height: 100%; position: absolute; background-color: black; top: 0%; left: 0%; transform: rotate(0deg) scale(1.005);"><source type="video/mp4" src="blob:https://x.com/6c9e2346-600e-48ba-b261-586f55d1ee29"></video>

![](https://pbs.twimg.com/amplify_video_thumb/2016958749647523843/img/JiDZx01_Kh206Dj-.jpg?name=large)

**Critiquing your writing and getting a response** prompt: "Use the playground skill to review my [SKILL.MD](https://skill.md/) and give me inline suggestions I can approve, reject or comment"

<video preload="none" tabindex="-1" playsinline="" aria-label="埋め込み動画" poster="https://pbs.twimg.com/amplify_video_thumb/2017023689385267200/img/T_nlh9qQTbEEHEan.jpg" style="width: 100%; height: 100%; position: absolute; background-color: black; top: 0%; left: 0%; transform: rotate(0deg) scale(1.005);"><source type="video/mp4" src="blob:https://x.com/c987cbee-0de2-42fd-be8a-ce9cd4f75a46"></video>

![](https://pbs.twimg.com/amplify_video_thumb/2017023689385267200/img/T_nlh9qQTbEEHEan.jpg?name=large)

**Tweaking a Remotion Video Intro** prompt: "Use the playground skill to tweak my intro screen to be more interesting and delightful"

<video preload="none" tabindex="-1" playsinline="" aria-label="埋め込み動画" poster="https://pbs.twimg.com/amplify_video_thumb/2016969186615185409/img/svQSGa99JPCBlrN6.jpg" style="width: 100%; height: 100%; position: absolute; background-color: black; top: 0%; left: 0%; transform: rotate(0deg) scale(1.005);"><source type="video/mp4" src="blob:https://x.com/c9e933f3-0c23-4826-a780-eafa3aeaa0ca"></video>

![](https://pbs.twimg.com/amplify_video_thumb/2016969186615185409/img/svQSGa99JPCBlrN6.jpg?name=large)

**Viewing an Architecture Diagram and letting the user comment** prompt: "Use the playground skill to show how this email agent codebase works and let me comment on particular nodes in the architecture to ask questions, make edits, etc"

<video preload="none" tabindex="-1" playsinline="" aria-label="埋め込み動画" poster="https://pbs.twimg.com/amplify_video_thumb/2016959674235703300/img/dRXEbTIov9kL2u9N.jpg" style="width: 100%; height: 100%; position: absolute; background-color: black; top: 0%; left: 0%; transform: rotate(0deg) scale(1.005);"><source type="video/mp4" src="blob:https://x.com/40a9b0b6-3ee7-4ae4-88f7-c4f664f4ee95"></video>

![](https://pbs.twimg.com/amplify_video_thumb/2016959674235703300/img/dRXEbTIov9kL2u9N.jpg?name=large)

**Balancing the Superhero Rogue-like game I'm making** prompt: "Use the playground skill to help me balance the 'Inferno' hero's deck"

<video preload="none" tabindex="-1" playsinline="" aria-label="埋め込み動画" poster="https://pbs.twimg.com/amplify_video_thumb/2016963678445457410/img/7wYwkhNTTh5LSmMi.jpg" style="width: 100%; height: 100%; position: absolute; background-color: black; top: 0%; left: 0%; transform: rotate(0deg) scale(1.005);"><source type="video/mp4" src="blob:https://x.com/28f18f34-2b00-4ba8-abab-1a0c5523fd4d"></video>

![](https://pbs.twimg.com/amplify_video_thumb/2016963678445457410/img/7wYwkhNTTh5LSmMi.jpg?name=large)

Excited to see how you all explore this! My tip for creating an interesting playground- think of a unique way of interacting with the model and then ask it to express that. I think you might find it surprising. If you make something cool, please share it!