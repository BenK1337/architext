# **✅ Architext AI - MVP Development Tasks**

This file tracks the development tasks for the Minimum Viable Product (MVP). Refer to the coding guidelines ([`./02-INSTRUCTIONS.md`](./02-INSTRUCTIONS.md)) 📐 for context. Update status (`[ ]` To Do, `[x]` Done, `[-]` Deferred/Blocked) manually as you proceed.

---

## **Phase 1: Project Setup & Core UI Shell** 🏗️

* `[ ]` **1.1 Project Initialization:** Create SvelteKit project (`npx create-svelte@latest`), install deps, init Git. Refer to /docs/08-PROJECT-STRUCTURE.md for project structure details.
* `[ ]` **1.2 CSS & PostCSS Setup:** Create CSS file structure (`src/lib/styles/...`), configure PostCSS (`vite.config.js` or `postcss.config.js` with autoprefixer), populate `theme.css` (CSS vars) & `global.css`. Import globals in root layout.
* `[ ]` **1.3 Dependency Installation:** Install Melt UI (`@melt-ui/svelte`), Lucide Icons (`lucide-svelte`), Supabase client libs (`@supabase/auth-helpers-sveltekit`, `@supabase/supabase-js`). 📦
* `[ ]` **1.4 Core Layout (`src/routes/+layout.svelte`):** Create main layout using semantic HTML, apply global layout styles. Ensure `<body>` scroll.
* `[ ]` **1.5 Basic Navigation Components:** Create `Header.svelte`, `Sidebar.svelte` (use CSS Modules for styling). Integrate into `+layout.svelte`.
* `[ ]` **1.6 Supabase Setup:** Create Supabase project, configure `.env` file, initialize Supabase client (`src/lib/supabaseClient.ts`). ☁️
* `[ ]` **1.7 Authentication UI:** Implement Login/Signup routes/UI using custom components styled with CSS Modules, calling Supabase Auth methods. Setup basic route protection (e.g., in root layout `load` function or hooks). 🔐

---

## **Phase 2: Core Feature UI Implementation** 🎨

* `[ ]` **2.1 Dashboard Page (`/`):** Create `+page.svelte`. Implement UI (Welcome, New Project button using Melt `createButton` + CSS Module, placeholder project list using custom Card component + CSS Module).
* `[ ]` **2.2 New Project Page/Modal (`/new` or modal):** Create route/component. Implement form UI (HTML elements styled with CSS Modules/global form styles). Include Name, Prompt, Platform, Language fields. Basic frontend validation.
* `[ ]` **2.3 Project Page (`/project/[id]`):** Create `+page.svelte`. Implement Tabbed interface (custom component potentially using Melt `createTabs` builder, styled w/ CSS Modules) for "Documentation" and "Tasks". Placeholders within tabs.
* `[ ]` **2.4 Document Display UI:** Implement interactive collapsible sections (custom component, potentially using Melt builder for accessibility, styled w/ CSS Modules). Implement Markdown rendering (e.g., `marked` library) and apply styles (custom CSS or PostCSS Typography plugin). 📄
* `[ ]` **2.5 Task Display UI:** Implement interactive task list with styled checkboxes (custom component styled w/ CSS Modules). ✅
* `[ ]` **2.6 Loading State UI:** Implement reusable loading indicators (spinners, skeletons styled w/ CSS). Implement detailed feedback messages UI. ⏳
* `[ ]` **2.7 Error Handling UI:** Implement custom Toast/Alert components (styled w/ CSS Modules) for informative errors. ⚠️

---

## **Phase 3: Backend Logic & Data (Supabase)** ☁️

* `[ ]` **3.1 Database Schema & RLS:** Define schema (`projects`, `generated_documents`, `tasks`, `users`) in Supabase SQL editor/migrations. Implement RLS (Simple User Ownership). Test RLS policies. 🔐
* `[ ]` **3.2 Mock AI Service Interface:** Create mock function (`src/lib/aiService.ts`) returning realistic structured Markdown/JSON. 🤖
* `[ ]` **3.3 `trigger-generation` Edge Function:** Create function. Implement logic (auth check, save initial project, call mock AI async, return status). Define/validate API payload. Add basic logging.
* `[ ]` **3.4 AI Response Handling Logic:** Implement logic (async part/separate function) to parse mock response, save docs/tasks to DB, update project status. Handle potential parsing/saving errors. Add logging.
* `[ ]` **3.5 `get-project-details` Edge Function:** Create function. Implement logic (auth check, fetch project data from DB, return). Define/validate API payload. Add basic logging.

---

## **Phase 4: Frontend Logic & Integration** 🔗

* `[ ]` **4.1 New Project Form Logic:** Implement form submission handler, call `trigger-generation` Edge Function, handle loading state, navigate on success.
* `[ ]` **4.2 Realtime/Polling Logic:** Implement Supabase Realtime subscription on Project page to listen for DB changes (e.g., project status, new docs/tasks). Update UI accordingly. ✨
* `[ ]` **4.3 Project Data Fetching:** Implement logic (e.g., in `load` function or `$effect`) to call `get-project-details` on initial load and potentially after Realtime update trigger. Handle loading/error states.
* `[ ]` **4.4 Data Rendering:** Implement logic to correctly parse/render fetched Markdown into collapsible sections. Implement logic to render task list from fetched data. Handle checkbox state changes visually (no backend update for MVP).
* `[ ]` **4.5 State Management:** Use Svelte Runes (`$state`, `$derived`) for component UI state. Use Stores for global state (e.g., user session) if needed.
* `[ ]` **4.6 Connect Loading/Error UI:** Connect UI components to actual loading/error states from API calls and Realtime updates.
* `[ ]` **4.7 Basic Navigation:** Implement navigation between pages using SvelteKit's `goto`. 🗺️

---

## **Phase 5: Testing & Refinement** ✨

* `[ ]` **5.1 E2E Testing:** Setup Playwright/Cypress. Write E2E tests for core flow (Login -> Create Project -> View Output). 🧪
* `[ ]` **5.2 Manual Testing:** Test thoroughly across Chrome, Firefox, Safari. Test responsive design. Test core functionality and edge cases found during dev. 👀
* `[ ]` **5.3 Refinement:** Fix bugs identified. Improve UI/UX based on testing. Code cleanup and refactoring based on guidelines.
* `[ ]` **5.4 Monitoring & Logging:** Review Supabase logs for errors during testing phase. Ensure logs provide useful info. 🪵
* `[ ]` **5.5 Deployment Prep:** Configure Supabase Hosting settings (custom domain?). Set production environment variables securely in Supabase dashboard. Run production build (`npm run build`) and test preview if possible. 🚀

---