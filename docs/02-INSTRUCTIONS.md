# **📐 Architext AI - Coding Instructions**

**Purpose:** This document outlines the essential coding guidelines, conventions, technology stack details, and project structure for the Architext AI application. Adherence to these instructions is crucial for maintaining code quality and consistency, especially when collaborating or using AI assistance.

## **📝 Overview**

Architext AI helps developers translate project ideas into structured plans using AI, creating a reliable "context foundation". This document details **how** to write code for this specific project, complementing the setup steps in [`./01-GETTING_STARTED.md`](./01-GETTING_STARTED.md) and the task list in [`./03-TASKS.md`](./03-TASKS.md).

## **💻 Tech Stack (MVP)**

* **Framework:** SvelteKit (2+)
* **UI Library:** Svelte (5+) with Melt UI (Headless Components)
* **Styling:** Custom CSS (Modules & Global files) with PostCSS (Autoprefixer)
    * **CSS Modules (`*.module.css`):** The **default** for component-specific styles (e.g., `Sidebar.svelte` uses `Sidebar.module.css`). Aim for BEM-like naming within modules where appropriate.
    * **Global CSS (`src/lib/styles/global.css`):** For base HTML element styles, resets, layout rules (e.g., body scrolling), and potentially global form styling. Imported in the root layout (`src/routes/+layout.svelte`).
    * **Theme Variables (`src/lib/styles/theme.css`):** Define CSS custom properties (variables) for colors, fonts, spacing, etc. Use these variables extensively in both module and global CSS files.
* **Language:** TypeScript (Strict Mode)
    * Enable `strict` mode in `tsconfig.json`.
    * Use explicit types for props, function signatures, API payloads, and store values. Avoid `any`.
* **Backend/DB:** Supabase
    * **Database:** PostgreSQL. Schema defined via Supabase SQL Editor or Migrations (Task 3.1). Key tables: `users`, `projects`, `generated_documents`, `tasks`.       
    * **Authentication:** Supabase Auth. Implement UI flows using Supabase client methods (Task 1.7).
    * **Backend Logic:** Edge Functions (Deno/TypeScript). Key functions: `trigger-generation`, `get-project-details` (Task 3.3, 3.5).
    * **Realtime:** Supabase Realtime Subscriptions for live UI updates on data changes (Task 4.2).
* **Icons:** Lucide Icons (`lucide-svelte`) (Task 1.3). Use appropriately sized icons.
* **Markdown Parsing:** Use a library like `marked` for rendering Markdown content fetched from the backend (Task 2.4). Apply custom styles for good readability. When using any markdown parser, ensure that user-generated content is sanitized to prevent XSS or other security issues.
* **Frontend Hosting:** Supabase Hosting.

## **📊 Project Status**

* MVP development phase. See [`./03-TASKS.md`](./03-TASKS.md) for detailed progress. ✅

## **🚀 Getting Started**

For initial project setup, cloning, dependency installation, and running the development server, please refer to the main guide:

➡️ **[`./01-GETTING_STARTED.md`](./01-GETTING_STARTED.md)**

This document (`02-INSTRUCTIONS.md`) focuses on the **coding guidelines, conventions, and detailed tech stack usage** you must follow *after* setup.

## **✍️ Coding Guidelines**

1.  **Code Style:** Follow the Prettier configuration defined in the project (`package.json` or `.prettierrc`). Run `npm run format` before committing. Consistent formatting is key! ✨
2.  **Linting:** Adhere to the ESLint configuration (`.eslintrc.cjs`). Run `npm run lint` to check for issues. Fix all linting errors before merging. Clean code is happy code! 😊
3.  **Naming Conventions:** Consistency is crucial here.
    * Components: `PascalCase.svelte` (e.g., `ProjectCard.svelte`, `DocumentSection.svelte`)
    * CSS Modules: `camelCase.module.css` (e.g., `projectCard.module.css`)
    * TypeScript files/functions: `camelCase.ts` / `camelCase()` (e.g., `parseMarkdown.ts`, `fetchProjectDetails()`)
    * Variables/Constants: `camelCase` / `UPPER_SNAKE_CASE` (e.g., `projectId`, `MAX_RETRIES`)
    * Database Tables/Columns: `snake_case` (e.g., `generated_documents`, `user_id`)
4.  **Component Structure:**
    * Keep components small, focused, and reusable. 🤔
    * Place reusable UI elements in `src/lib/components`.
    * Use SvelteKit's routing conventions (`src/routes`). Page components (`+page.svelte`), layouts (`+layout.svelte`), server logic (`+page.server.ts`, `+layout.server.ts`).
    * Utilize Melt UI builders for headless logic (e.g., `createButton` (Task 2.1), `createTabs`? (Task 2.3), `createCollapsible` (Task 2.4)) and apply custom styles via CSS Modules.
5.  **State Management:** Choose the right tool for the job.
    * **Component State:** Use Svelte 5 Runes (`$state`, `$derived`) for local component UI state (e.g., form inputs, loading flags) (Task 4.5).
    * **Shared/Global State:** Use Svelte Stores (`src/lib/stores`) for state shared across components/routes (e.g., user session, global notifications) (Task 4.5). Keep stores focused.
6.  **API Interaction (Supabase):**
    * Initialize and export the Supabase client from `src/lib/supabaseClient.ts` (Task 1.6).
    * Call Edge Functions using `supabase.functions.invoke('function-name', { body: payload })`. Define clear TypeScript interfaces for payloads and responses.
    * Implement data fetching in SvelteKit `load` functions or using `$effect.root` client-side where appropriate (Task 4.3).
    * Handle loading states (Task 2.6, 4.6) and errors robustly using `try/catch`. Display user-friendly messages via custom Toast/Alert components (Task 2.7, 4.6). ⚠️
7.  **Styling Implementation:**
    * **UI Replication Goal:** The primary target is to replicate the look, feel, and behavior of **Google Agentspace ([cloud.google.com/products/agentspace](https://cloud.google.com/products/agentspace)) / AI Studio ([aistudio.google.com](https://aistudio.google.com/))**. Pay close attention to details, using resources like [ai.google.dev](https://ai.google.dev/) for broader context.
    * **Reference Materials:** Use screenshots, notes, and collected assets stored in the `/design_examples/` directory (relative to project root) as the visual guide.
    * **Design System Elements:** Identify and consistently apply specific design elements from the target UI, including:
        * Color palettes (including specific shades for states like hover, active, disabled).
        * Typography (font families, sizes, weights, line heights).
        * Spacing and layout principles (margins, padding, grid usage).
        * **Gradients:** Replicate any gradients used accurately. Define standard gradients in `theme.css` if possible.
        * Border-radius and shadows.
        * Component states (hover, focus, active, disabled) must match the reference UI's visual feedback.
        * **Micro-interactions** and animations (subtle transitions, loading indicators, etc.).
    * **Implementation:**
        * **Prioritize CSS Modules** for component encapsulation. Avoid style conflicts! 🛡️
        * Use `src/lib/styles/theme.css` for all core design tokens (colors, fonts, spacing variables, standard gradients).
        * Use `src/lib/styles/global.css` minimally for base element styling, layout helpers, and form resets.
        * Apply styles consistently according to UI designs (see images in `/design_examples/`). Create reusable components for common UI patterns (Cards, Buttons, Tabs, Task Items, Loading Indicators, Toast/Alert etc.) (Tasks 2.1, 2.3, 2.4, 2.5, 2.6).
    * **Inspection:** Inspecting the CSS/DOM of AI Studio can be a useful reference, but be mindful that its underlying framework and CSS may differ significantly. Focus on replicating the visual outcome.
8.  **TypeScript Usage:** Maximize type safety. 💪
    * Define interfaces/types for all data structures (DB rows, API payloads/responses, props, stores) in `src/lib/types` or colocated where appropriate.
    * Use TypeScript in Svelte components (`<script lang="ts">`).
    * Leverage TypeScript in SvelteKit `load` functions and server routes.
    * Write Edge Functions in TypeScript.
9.  **Error Handling:** Be prepared! 🛡️
    * Use `try/catch` blocks for API calls and potentially failing logic.
    * Implement SvelteKit's `+error.svelte` pages for handling application-level errors gracefully.
    * Provide clear user feedback for errors using dedicated UI components (Task 2.7).
    * Add meaningful logging (client `console.error`, server/Edge Function logs) for debugging (Tasks 3.3, 3.4, 3.5). `console.log` is your friend during development! 🐞
10. **Accessibility (a11y):** Build for everyone. 🌍
    * Use semantic HTML (`<nav>`, `<main>`, `<button>`, etc.).
    * Ensure keyboard navigation and focus states are clear.
    * Use ARIA attributes correctly, especially with Melt UI.
    * Test with screen readers periodically.
    * Use the [WAI accessibility checklist](https://www.w3.org/WAI/test-evaluate/) for periodic accessibility reviews.
11. **Comments:** Explain the 'why', not just the 'what'. 💡
    * Write clear comments for complex logic, assumptions, or workarounds.
    * Use JSDoc comments for functions, components, and types (`/** ... */`).
    * Mark temporary code or areas needing future work with `// TODO: [description]`.
12. **Testing:** Ensure reliability. ✅
    * **Unit Tests:** Use Vitest for utility functions (e.g., `src/lib/utils/parseMarkdown.ts`). Place all test files in `/tests/unit/`.
    * **E2E Tests:** Use Playwright or Cypress (Task 5.1) for critical user flows (Login -> Create Project -> View Output). Place all E2E test files in `/tests/e2e/`.
    * **Manual Testing:** Test thoroughly across target browsers (Chrome, Firefox, Safari) and screen sizes (Task 5.2).
13. **Git Workflow:** Collaborate effectively. 🤝
    * **Branching:** Feature branches off `main` (e.g., `feat/implement-auth-ui`, `fix/sidebar-layout`).
    * **Commits:** Use Conventional Commits format (`feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:`). Write clear messages.
    * **Pull Requests:** Use PRs to merge into `main`. Require reviews if collaborating.
14. **Supabase Specifics:** Leverage the platform wisely. ☁️
    * **Schema:** Use Supabase Studio SQL Editor or DB Migrations (`supabase/migrations`) (Task 3.1). Keep schema documented or inferable.
    * **RLS:** Implement Row-Level Security policies for all user-specific data tables. Primary strategy: User Ownership (`user_id` column matching `auth.uid()`) (Task 3.1). Test policies! 🔐
    * **Edge Functions:** Structure clearly. Include authentication checks. Implement input validation and robust error handling/logging (Task 3.3, 3.5). Use environment variables for secrets.
    * **Realtime:** Implement subscriptions carefully, ensuring efficient updates and proper cleanup (Task 4.2).
15. **Dependencies:** Manage carefully. 📦
    * Keep dependencies reasonably updated (`npm update`). Check changelogs for breaking changes.
    * Review the purpose and necessity of any new dependency before adding it.
16. **Environment Variables:** Secure and organized. 🔑
    * Define all necessary environment variables in `.env.example`.
    * Load them correctly in SvelteKit using `$env/static/public` or `$env/dynamic/private`.
    * **Never commit `.env` files to Git!** Add `.env` to your `.gitignore` file.

## **🙌 Contributing**

*(Placeholder for contribution guidelines - to be added later if applicable)*

## **📄 License**

*(Placeholder for license information - e.g., MIT, Apache 2.0)*