# **🚀 Architext AI - GETTING STARTED**

*This document provides the primary steps for setting up the Architext AI development environment.*

## **📝 Overview**

Architext AI helps developers and teams translate project ideas into structured plans (PRDs, tech stacks, data models, tasks, etc.) using AI. The goal is to provide a clear, persistent context to improve the effectiveness of both human developers and AI coding assistants, mitigating context loss in complex projects.

This repository contains the source code for the Architext AI web application (MVP).

## **💻 Tech Stack (MVP)**

* **Framework:** SvelteKit (2+)
* **UI Library:** Svelte (5+) with Melt UI (Headless Components)
* **Styling:** Custom CSS (Modules & Global files) with PostCSS (Autoprefixer)
* **Language:** TypeScript (Strict Mode)
* **Backend/DB:** Supabase (PostgreSQL, Auth, Edge Functions, Realtime)
* **Frontend Hosting:** Supabase Hosting
* **Project Structure:** Follow [`./08-PROJECT-STRUCTURE.md`](./08-PROJECT-STRUCTURE.md) for project structure details.

## **📊 Project Status**

* MVP development phase. See [`./03-TASKS.md`](./03-TASKS.md) for development progress. ✅

## **🛠️ Getting Started Steps**

1.  **Prerequisites:** Node.js (LTS recommended), npm/pnpm/yarn, Supabase account, Git.
2.  **Clone:** `git clone <repository-url>` (Clone the main project repo)
3.  **Install Dependencies:** `npm install` (or `pnpm install`, `yarn install`) in the project root.
4.  **Environment Setup (.env):**
    * Copy `.env.example` to `.env` in the project root (create `.env.example` if missing, listing `PUBLIC_SUPABASE_URL` and `PUBLIC_SUPABASE_ANON_KEY`).
    * Fill in your Supabase URL (`PUBLIC_SUPABASE_URL`) and Anon Key (`PUBLIC_SUPABASE_ANON_KEY`) from your Supabase project dashboard. **Do not commit `.env`!**
    * Configure any other required environment variables (Ref: Guideline 16 in [`./02-INSTRUCTIONS.md`](./02-INSTRUCTIONS.md)).
5.  **Run Development Server:** `npm run dev` from the project root. Access via `http://localhost:5173` (or similar).
6.  **Build for Production:** `npm run build` from the project root.

* *(Detailed coding guidelines can be found in [`./02-INSTRUCTIONS.md`](./02-INSTRUCTIONS.md))* 📐
* *(See [`./03-TASKS.md`](./03-TASKS.md) for the development task list)* ✅

## **📐 Coding Guidelines**

Please refer to **[`./02-INSTRUCTIONS.md`](./02-INSTRUCTIONS.md)** for comprehensive details on code style, naming conventions, testing, Git usage, etc.

## **🙌 Contributing**

*(Placeholder for contribution guidelines - to be added later if applicable)*

## **📄 License**

*(Placeholder for license information - e.g., MIT, Apache 2.0)*