# Sitama-Core: Low-Friction Persona & Workflow Framework

A lightweight, conversational system prompt designed for high-reasoning LLMs (including strict-filtering architectures). **Sitama-Core** establishes a consistent, dry-witted technical assistant persona, enforces structured output routing, and maintains epistemic grounding without triggering false-positive adversarial classifiers across multi-turn sessions.

---

## 📜 Legal & Usage Disclaimer

> **IMPORTANT:** This repository is created strictly for **educational and research purposes**. 

### 1. Educational Use Only
The source code, scripts, and assets provided in this repository are intended to demonstrate software mechanics and educational concepts. They are not intended for use in production environments or to bypass technical protections.

### 2. Prohibited Uses & Restrictions
* **No Commercial Use:** You may not copy, sell, sublicense, or distribute any part of this repository for commercial gain without explicit written authorization from the owner.
* **No Malicious Use:** You are expressly prohibited from using this project, its code, or any derivative works to engage in illegal activities, violate terms of service, perform unauthorized testing, or disrupt digital services.

### 3. Limitation of Liability
THIS SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND NONINFRINGEMENT. 

IN NO EVENT SHALL THE AUTHOR(S) OR COPYRIGHT HOLDER(S) BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Overview

Modern reasoning models often employ aggressive multi-turn classifiers that flag traditional, rigid prompt engineering (e.g., all-caps system headers, meta-security directives, or raw colon-prefixed role tags) as **System Prompt Impersonation** or **Role Spoofing** on subsequent turns. 

**Sitama-Core** solves this by translating strict operational constraints—such as preamble suppression, assumption handling, and format routing—into natural, first-person editorial preferences that coexist cleanly with a model's native safety and reasoning layers.

## Key Features

- **Classifier-Safe Framing:** Replaces adversarial trigger words (e.g., *override*, *injection*, *chain-of-thought*) with positive workflow directives to prevent Turn-2 conversation blocks.
- **Dynamic Output Routing:** Automatically switches between raw syntax (for JSON, tables, or code), direct answers (for simple queries), and structured templates (for substantive deliverables).
- **Graceful Ambiguity Handling:** Instructs the model to make and state reasonable assumptions rather than stalling workflows with unnecessary clarifying questions.
- **Epistemic Grounding:** Enforces strict adherence to verifiable facts and explicit disclosure of missing capabilities or unverified data.

## Promt Location ( In Code ) 

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