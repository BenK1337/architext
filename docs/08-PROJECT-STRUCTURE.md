# **🏗️ Architext AI - Project Structure**

architext/
├── docs/
│   ├── design_examples/
│   │   └── [your design examples]
│   ├── 00-OVERVIEW.md
│   ├── 01-GETTING_STARTED.md
│   ├── 02-INSTRUCTIONS.md
│   ├── 03-TASKS.md
│   ├── 04-HISTORY.md
│   ├── 05-CHANGELOG.md
│   ├── 06-AI_CONTEXT_PROMPT.md
│   ├── 07-TROUBLESHOOTING.md
│   └── 08-PROJECT-STRUCTURE.md
├── src/
│   ├── lib/
│   │   ├── components/
│   │   │   ├── Button/
│   │   │   │   ├── Button.svelte
│   │   │   │   └── Button.module.css
│   │   │   ├── Card/
│   │   │   │   ├── Card.svelte
│   │   │   │   └── Card.module.css
│   │   │   ├── Header/
│   │   │   │   ├── Header.svelte
│   │   │   │   └── Header.module.css
│   │   │   ├── Sidebar/
│   │   │   │   ├── Sidebar.svelte
│   │   │   │   └── Sidebar.module.css
│   │   │   └── TaskItem/
│   │   │       ├── TaskItem.svelte
│   │   │       └── TaskItem.module.css
│   │   ├── server/
│   │   │   └── [your server-only lib files]
│   │   ├── styles/
│   │   │   ├── global.css
│   │   │   └── theme.css
│   │   ├── utils/
│   │   │   ├── parseMarkdown.ts
│   │   │   └── [other utility functions]
│   │   └── supabaseClient.ts
│   ├── routes/
│   │   ├── +layout.svelte
│   │   ├── +layout.ts
│   │   ├── +page.svelte
│   │   ├── +page.ts
│   │   ├── auth/
│   │   │   ├── login/
│   │   │   │   ├── +page.svelte
│   │   │   │   └── +page.ts
│   │   │   └── signup/
│   │   │       ├── +page.svelte
│   │   │       └── +page.ts
│   │   ├── new/
│   │   │   ├── +page.svelte
│   │   │   └── +page.ts
│   │   └── project/
│   │       └── [id]/
│   │           ├── +page.svelte
│   │           └── +page.ts
│   └── app.html
├── static/
│   ├── favicon.png
│   └── [other static assets]
├── supabase/
│   └── migrations/
│       └── [your SQL migration files]
├── tests/
│   ├── unit/
│   │   └── [your unit tests]
│   └── e2e/
│       └── [your e2e tests]
├── .env.example
├── .eslintrc.cjs
├── .gitignore
├── .prettierrc
├── package.json
├── postcss.config.cjs
├── README.md
├── svelte.config.js
├── tsconfig.json
└── vite.config.ts

## 🧪 Testing

All test files should be placed in the `/tests` directory:
- Unit tests: `/tests/unit/`
- E2E tests: `/tests/e2e/`

This keeps the codebase organized and makes it easy to locate and run tests.
