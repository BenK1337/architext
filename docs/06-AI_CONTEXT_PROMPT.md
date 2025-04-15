# **🤖 Architext AI - AI Context Prompt Template**

**Purpose:** Use this template to provide essential context to an AI assistant (like ChatGPT, Claude, Gemini, or Copilot) when asking for help with development tasks related to the Architext AI project. Fill in the **Critical Setup Details** and confirm/define the **Current Task / Goal** section before using.

## **📌 Project Overview**

You are assisting with the **Architext AI** project.

**Goal:** Architext AI is a web application that helps developers plan projects by generating structured documentation (PRDs, tech stacks, tasks, etc.) from initial ideas using AI. Its core purpose is to create a reliable "context foundation" to improve development workflow and mitigate context loss, especially when using AI coding tools.

**MVP Scope:** The current focus is the Minimum Viable Product (MVP), which is a cloud-hosted application built with SvelteKit and Supabase. Key MVP features include user auth, project creation via prompt, AI generation of core documents & tasks (mocked initially), and displaying these in the UI.

## **📚 Key Documentation Links (Relative paths within `/docs`)**

Refer to these primary documents for project details:

* **Project Goals & Scope Index:** [`./00-OVERVIEW.md`](./00-OVERVIEW.md) 🧭
* **Setup Guide:** [`./01-GETTING_STARTED.md`](./01-GETTING_STARTED.md) 🚀
* **Detailed Coding Standards & Tech Stack Usage:** [`./02-INSTRUCTIONS.md`](./02-INSTRUCTIONS.md) (CRITICAL: Adhere to these guidelines) 📐
* **Current Development Tasks:** [`./03-TASKS.md`](./03-TASKS.md) ✅
* **Development History / Milestones:** [`./04-HISTORY.md`](./04-HISTORY.md) 📜
* **Project Changelog:** [`./05-CHANGELOG.md`](./05-CHANGELOG.md) 📢
* **Troubleshooting Guide:** [`./07-TROUBLESHOOTING.md`](./07-TROUBLESHOOTING.md) 🛠️
* **Target UI Design Reference:** [`/design_examples/`](/design_examples/) (Visual guide based on Google Agentspace, [AI Studio](https://aistudio.google.dev), [AI Google Resources](https://ai.google.dev) ) 🎨     

## **💻 Core Tech Stack Summary**

* **Frontend:** SvelteKit (2+), Svelte (5+), Melt UI (Headless), Custom CSS (Modules/Global), PostCSS, TypeScript
* **Backend:** Supabase (PostgreSQL, Auth, Edge Functions, Realtime)
* **Language:** TypeScript (Strict Mode)

## **🔑 Critical Setup Details (User: Fill before use)**

* **Supabase URL:** `[Your PUBLIC_SUPABASE_URL Here]`
* **Supabase Anon Key:** `[Your PUBLIC_SUPABASE_ANON_KEY Here]`

## **🧠 Project Context (AI: Infer from Docs)**

* **Database Schema Notes:** Understand the planned schema (key tables: `users`, `projects`, `generated_documents`, `tasks`) by referring to the feature descriptions in `00-OVERVIEW.md` and the coding guidelines in `02-INSTRUCTIONS.md`. Note that the detailed schema evolves during development (see `03-TASKS.md`).
* **Key API Endpoints (Edge Functions):** Identify key planned Edge Functions (like `trigger-generation`, `get-project-details`) and their purpose by reviewing `00-OVERVIEW.md` and `03-TASKS.md`. Note that exact payloads are defined during implementation.

## **🎯 Current Task / Goal (AI Suggests, User Confirms/Defines)**

_Last updated: 2025-04-15_


**AI Action:** Review [`./03-TASKS.md`](./03-TASKS.md). Find the last task marked `[x]` (Done). Then, find the **first subsequent task** in the list that is marked `[ ]` (To Do), skipping any tasks marked `[-]` (Deferred/Blocked). If no tasks are marked `[x]`, suggest the very first task marked `[ ]`. State the title of this identified task below as a suggestion.

**Suggested Next Task (AI to fill):** `[AI Suggests Task Title based on analysis of TASKS.md]`

**User Action:** Please confirm if the suggested task above is correct, **OR** clearly describe the specific task, code section, or question you need assistance with *right now* in the `CURRENT_FOCUS` block below. _Only one task should be specified at a time; tasks should be completed one after another, not in parallel._ Providing your specific focus is essential for getting relevant assistance, as the AI cannot know your exact immediate need or handle situations outside the suggested linear flow (like bug fixing or revisiting deferred tasks) without your explicit direction.

* **CURRENT\_FOCUS:** `[User confirms suggested task by writing 'Yes, proceed with suggested task' OR describes their specific focus here, e.g., 'Fix bug in Sidebar.svelte related to task 1.5' OR 'Implement task 2.4: Document Display UI']`
    * *Example (If confirming):* Yes, proceed with suggested task.
    * *Example (If specifying):* Implement the frontend logic in `src/routes/project/[id]/+page.svelte` to fetch project details using the `get-project-details` Edge Function and display the tasks in a list using CSS Modules for styling, according to the guidelines in `02-INSTRUCTIONS.md`.
    * *Example (If specifying):* Write unit tests using Vitest for the utility function `src/lib/utils/parseMarkdown.ts`, following testing guidelines in `02-INSTRUCTIONS.md`.
    * *Example (If specifying):* Refactor the CSS in `src/lib/components/ProjectCard.module.css` to better align with BEM and the custom theme variables defined in `src/lib/styles/theme.css`.

## **⚠️ CRITICAL INSTRUCTION TO AI ASSISTANT**

**Before generating any code, suggestions, or answers, you MUST thoroughly read and understand the context provided in the linked documents:** `00-OVERVIEW.md` (for scope/goals), `02-INSTRUCTIONS.md` (for ALL coding standards, conventions, and tech stack usage), and `03-TASKS.md` (for overall task context). Also consult `04-HISTORY.md` and `05-CHANGELOG.md` if relevant to the query. **Adhere strictly to the project's established guidelines and technology stack.** Your primary goal is to assist with the specific **'Current Task / Goal'** confirmed or defined by the user above, using the provided documentation as your definitive context and source of truth for project standards. Prioritize solutions that fit within the existing architecture.