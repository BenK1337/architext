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

* **Supabase URL:** `https://betvkqxsvkjaxyopesyi.supabase.co`
* **Supabase Anon Key:** `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImJldHZrcXhzdmtqYXh5b3Blc3lpIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDQ2MzA1NTcsImV4cCI6MjA2MDIwNjU1N30.8gvfnr9a3FX3uhYy4zuBj8WEy_jxOVGCG1KJtco7fvQ`

## **🧠 Project Context (AI: Infer from Docs)**

---

## **✨ Recent UI/UX Improvements**

- The landing (dashboard) page now uses a modern, centered flexbox layout for a polished, professional look.
- Login logic now uses the correct Supabase Provider type, fixing previous TypeScript errors.
- Layout and component alignment is consistent across the shell, sidebar, and top bar.
- All content and labels are Architext-specific, following branding guidelines.

---

* **Database Schema Notes:** Understand the planned schema (key tables: `users`, `projects`, `generated_documents`, `tasks`) by referring to the feature descriptions in `00-OVERVIEW.md` and the coding guidelines in `02-INSTRUCTIONS.md`. Note that the detailed schema evolves during development (see `03-TASKS.md`).
* **Key API Endpoints (Edge Functions):** Identify key planned Edge Functions (like `trigger-generation`, `get-project-details`) and their purpose by reviewing `00-OVERVIEW.md` and `03-TASKS.md`. Note that exact payloads are defined during implementation.

## **🎯 Current Task / Goal (Open & Closed Tasks Overview)**

_Last updated: 2025-04-15_

### ✅ Completed Tasks (Closed)
- 1.1 Project Initialization
- 1.2 CSS & PostCSS Setup
- 1.5 Basic Navigation Components
- 1.6 Supabase Setup
- A2. Replicate Google AI Studio UI
  - Landing/dashboard page is now centered and visually polished
  - Login provider type fix (Supabase Provider type)
  - Layout and component alignment is consistent and on-brand

### 🟡 Open Tasks (To Do)
- 1.3 Dependency Installation: Install Melt UI, Lucide Icons, Supabase client libs
- 1.4 Core Layout (`src/routes/+layout.svelte`): Main layout and global styles
- A1. Enable Providers in Supabase (GitHub, Google, Passkeys)
- A2.1 Sidebar: Left sidebar with logo, navigation, footer
- A2.2 Main Prompt Area: Headline, prompt input, suggestion chips, Run button
- A2.3 Top Bar: Top navigation with avatar, settings, links
- A2.4 Right Sidebar: Run/settings panel
- A2.5 Profile Menu: Avatar dropdown, user info, switch/logout
- A3. Auth Integration: Supabase Auth in SvelteKit, session management, route protection
- A4. User Info & Logout: Show user info and logout button
- A5. Test Auth Flows
- 1.7 Authentication UI: Login/Signup routes, route protection
- 2.1 Dashboard Page (`/`): +page.svelte, UI, project list
- 2.2 New Project Page/Modal: Form UI, validation
- 2.3 Project Page (`/project/[id]`): Tabbed interface for Documentation/Tasks
- 2.4 Document Display UI: Collapsible sections, Markdown rendering, styles
- 2.5 Task Display UI: Task list with styled checkboxes
- 2.6 Loading State UI: Loading indicators, feedback messages
- 2.7 Error Handling UI: Toast/Alert components
- 3.1 Database Schema & RLS: Define schema, implement/test RLS
- 3.2 Mock AI Service Interface
- 3.3 `trigger-generation` Edge Function
- 3.4 AI Response Handling Logic
- 3.5 `get-project-details` Edge Function
- 4.1 New Project Form Logic
- 4.2 Realtime/Polling Logic
- 4.3 Project Data Fetching
- 4.4 Data Rendering
- 4.5 State Management
- 4.6 Connect Loading/Error UI
- 4.7 Basic Navigation
- 5.1 E2E Testing
- 5.2 Manual Testing
- 5.3 Refinement
- 5.4 Monitoring & Logging
- 5.5 Deployment Prep

---

**How to use:**
- Select the next actionable task from the open list above and specify it in the CURRENT_FOCUS below.
- Only one task should be specified at a time. Tasks should be completed sequentially, not in parallel.
- Example: `Implement task 2.4: Document Display UI`

---

## **🧠 AI Context Window Policy**

- The AI will monitor its context window and proactively warn the user if the context is nearing its limit.
- If the context window is close to being filled, the AI will alert the user and recommend summarizing or archiving less relevant information.
- This policy is actively reflected in the docs and in real-time interactions to ensure no critical information is lost during development.

**User Action:** Please confirm if the suggested task above is correct, **OR** clearly describe the specific task, code section, or question you need assistance with *right now* in the `CURRENT_FOCUS` block below. _Only one task should be specified at a time; tasks should be completed one after another, not in parallel._ Providing your specific focus is essential for getting relevant assistance, as the AI cannot know your exact immediate need or handle situations outside the suggested linear flow (like bug fixing or revisiting deferred tasks) without your explicit direction.

* **CURRENT\_FOCUS:** `[User confirms suggested task by writing 'Yes, proceed with suggested task' OR describes their specific focus here, e.g., 'Fix bug in Sidebar.svelte related to task 1.5' OR 'Implement task 2.4: Document Display UI']`
    * *Example (If confirming):* Yes, proceed with suggested task.
    * *Example (If specifying):* Implement the frontend logic in `src/routes/project/[id]/+page.svelte` to fetch project details using the `get-project-details` Edge Function and display the tasks in a list using CSS Modules for styling, according to the guidelines in `02-INSTRUCTIONS.md`.
    * *Example (If specifying):* Write unit tests using Vitest for the utility function `src/lib/utils/parseMarkdown.ts`, following testing guidelines in `02-INSTRUCTIONS.md`.
    * *Example (If specifying):* Refactor the CSS in `src/lib/components/ProjectCard.module.css` to better align with BEM and the custom theme variables defined in `src/lib/styles/theme.css`.

## **⚠️ CRITICAL INSTRUCTION TO AI ASSISTANT**

**Before generating any code, suggestions, or answers, you MUST thoroughly read and understand the context provided in the linked documents:** `00-OVERVIEW.md` (for scope/goals), `02-INSTRUCTIONS.md` (for ALL coding standards, conventions, and tech stack usage), and `03-TASKS.md` (for overall task context). Also consult `04-HISTORY.md` and `05-CHANGELOG.md` if relevant to the query. **Adhere strictly to the project's established guidelines and technology stack.** Your primary goal is to assist with the specific **'Current Task / Goal'** confirmed or defined by the user above, using the provided documentation as your definitive context and source of truth for project standards. Prioritize solutions that fit within the existing architecture.