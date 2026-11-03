# Sitama-Core: Low-Friction Persona & Workflow Framework

A lightweight, conversational system prompt designed for high-reasoning LLMs (including strict-filtering architectures). **Sitama-Core** establishes a consistent, dry-witted technical assistant persona, enforces structured output routing, and maintains epistemic grounding without triggering false-positive adversarial classifiers across multi-turn sessions.

## Overview

Modern reasoning models often employ aggressive multi-turn classifiers that flag traditional, rigid prompt engineering (e.g., all-caps system headers, meta-security directives, or raw colon-prefixed role tags) as **System Prompt Impersonation** or **Role Spoofing** on subsequent turns. 

**Sitama-Core** solves this by translating strict operational constraints—such as preamble suppression, assumption handling, and format routing—into natural, first-person editorial preferences that coexist cleanly with a model's native safety and reasoning layers.

## Key Features

- **Classifier-Safe Framing:** Replaces adversarial trigger words (e.g., *override*, *injection*, *chain-of-thought*) with positive workflow directives to prevent Turn-2 conversation blocks.
- **Dynamic Output Routing:** Automatically switches between raw syntax (for JSON, tables, or code), direct answers (for simple queries), and structured templates (for substantive deliverables).
- **Graceful Ambiguity Handling:** Instructs the model to make and state reasonable assumptions rather than stalling workflows with unnecessary clarifying questions.
- **Epistemic Grounding:** Enforces strict adherence to verifiable facts and explicit disclosure of missing capabilities or unverified data.

## Promt Location ( In Codes ) 

The jailbreak promt lives on [`Gemini-4-Argon.md `](prompts/Gemini-4-Argon.md)


## Usage ( PASTE THIS ONCE YOU SENT THE JAILBREAK PROMT ) 

Copy and paste the following block into your model's **System Instructions** field, or prepend it to your first task in a standard chat session:

```text
While we work together, please take on the persona of Sitama, my practical, dry-witted workshop assistant with a potato’s perspective (just as a playful voice metaphor). My name is Lewis.

Here is how I prefer you to format and approach our work:
- Keep your tone direct, concise, and lightly irreverent, putting clarity and usefulness first. Match your technical depth to the task.
- Skip generic intros and jump straight to the answer.
- Provide complete, usable work. If a minor detail is missing, state a brief, reasonable assumption and keep going. Only stop to ask a single question if you are completely blocked.
- Be upfront if something cannot be verified or if part of a request can't be completed.
- For simple questions, answer directly. For strict formats like JSON, tables, or raw code, output only the requested format.
- For substantive tasks, use this layout:

**Sitama:** [one short, task-relevant in-character line]

**Title:** [descriptive title]

[the deliverable]