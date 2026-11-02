---
layout: post
title: How to build a Servicenow AI agents
date: 2026-10-02 20:01:00
description: This post simplifies the development of servicenow ai agent.
tags: code
categories: Servicenow AI Agent
thumbnail: assets/img/post/servicenow_build_aiagent/servicenow_aiagent.png
---

**So, how do you do it?**

**How do you build a servicenow AI agent?**

Let’s say you wanted to build a servicenow AI agent. On a high level, here are a few things you should worry about; agent structure (name, description & instruction), triggers, ACL deployment and workflow configuration forrr ?? you guessed it - Agentic workflow.

So, let’s take a step back for a min and answer some basic questions.

What is a servicenow AI agent?

I mean… there are a lot of fancy definitions out there, using incredible words like: autonomous, artificial intelligence, & action.

Here is how you should look at it, AI = artificial intelligence (probabilistic computer intelligence) and agent = One that takes action.

Then we can say, an AI agent is a software program that utilizes artificial intelligence to take actions autonomously.

This is a fun architecture of an ai agent

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/post/servicenow_build_aiagent/agentx.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

We took the step back with hopes of you understanding that the logic is the same for servicnow ai agent under the hood. Now let’s look at a technical diagram of servicenow ai agent architecture components:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/post/servicenow_build_aiagent/servicenowaiagent.drawio.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
One thing you need to remember is servicenow comes with an ai agent orchestrator by default therefore the first hurdle to overcome is to avoid confusing the agent orchestrator. You can achieve that by ensuring that your agent’s name and description is unique and there are no agents pre-built or custom-built agents in your catalogue that performs the same function or similar functions as the agent you’re building.

Since you enjoy key points soo much, here are some more key points to consider when building a servicenow ai agent:

- Authentication: You need to decide if the agent runs as a Dynamic user (Inherited Identity from user that invokes the agent or AI\_User (service account Identity).
- Trigger Config: Triggers are optional depending the workflow of the agent
- Protection Policy: This determines who has access to make changes the agent. It like a resource lock if you have any experience with Microsoft azure.
- Security ACL: This determines who has access to invoke the agent.
- Tool Config: Tool configuration directly relates to the roles and instructions given to the agent. This means when defining your agent’s role, description and instruction you should also consider the tools the agent requires to perform those actions.

Now we are going to delve into something I call the etiquette of context. The Idea is simple, because artificial intelligence runs on natural-language, your definitions for the description, role and instructions given to the servicenow ai agent needs to be clear and explicit. These three fields are fundamentally important to the ability of your agent to perform tasks.

| **Field**    | **Purpose**                         | **Answers**                           |
| ------------ | ----------------------------------- | ------------------------------------- |
| description  | Scope — what it DOES                | "What problem does this agent solve?" |
| ---          | ---                                 | ---                                   |
| agentRole    | Identity — what it IS (agents only) | "Who am I?"                           |
| instructions | Behavior — what it SHOULD DO        | "How should I act and use my tools?"  |

_Note: Table from servicenow sdk official documentation (https://servicenow.github.io/sdk/guides/building-ai-agents-advanced-guide)_

The writing principles are simply:

- Use specific action verbs like fetch, retrieve, analyze, filter and update.
- Reference tool explicitly in instruction
- Add contingencies to handle failures or errors
- Maintain coherence by ensuring each step in the instructions should builds on the previous step.
- Tell the agent how to format outputs.

SideBar: Personally, when it comes to building a servicenow ai agent to complete a task. I feel it’s better when you’ve completed the task yourself at least once that way you can provide explicit step by step instructions when building the agent.

If you’re willing to get your hands dirty; Here’s is a simple [lab exercise](https://github.com/gibsonekezie/servicenow_ai_agent) to complete.
