# **🛠️ Architext AI - Troubleshooting Guide**

This document lists common issues encountered during setup or development and their potential solutions. If your issue isn't listed, check Supabase logs and browser dev tools!

## **Environment & Setup Issues** ⚙️

* **Issue:** `Error: Cannot find module 'dotenv'` or environment variables (`PUBLIC_SUPABASE_URL`, etc.) are undefined.
    * **Solution 1:** Ensure you have run `npm install` (or `pnpm install`/`yarn install`) after cloning.
    * **Solution 2:** Verify you have copied `.env.example` to a file named exactly `.env` in the project **root directory** (the same directory as `package.json`).
    * **Solution 3:** Make sure the `.env` file contains the correct variable names (`PUBLIC_SUPABASE_URL`, `PUBLIC_SUPABASE_ANON_KEY`) and that you have pasted your actual keys/URL from the Supabase dashboard without extra spaces or characters.
    * **Solution 4:** **Restart the development server** (`npm run dev`) after creating or modifying the `.env` file. SvelteKit often requires a restart to load new environment variables.

* **Issue:** Invalid Supabase URL or Anon Key errors during runtime (e.g., 401 Unauthorized, fetch errors).
    * **Solution:** Double-check that `PUBLIC_SUPABASE_URL` and `PUBLIC_SUPABASE_ANON_KEY` in your `.env` file **exactly match** the values from your Supabase project dashboard (Settings -> API). Ensure there are no typos or extra characters.

## **Build & Runtime Errors** 💥

* **Issue:** TypeScript errors during `npm run dev` or `npm run build`.
    * **Solution 1:** Read the error message carefully! It often points to the exact file and line number. 🧐
    * **Solution 2:** Ensure all function arguments and variable assignments match their expected types. Check for `null` or `undefined` values where objects are expected.
    * **Solution 3:** Run `npm run check` or `npx tsc --noEmit` to get a list of all TypeScript errors in the project.

* **Issue:** CSS Modules not applying styles (seeing `[object Object]` class names, styles missing).
    * **Solution 1:** Ensure your CSS file is named correctly (`*.module.css`).
    * **Solution 2:** Verify you are importing the styles correctly in your Svelte component: `import styles from './MyComponent.module.css';`
    * **Solution 3:** Check that you are applying the styles using the imported object: `<div class={styles.myClass}>...</div>`. Ensure the class name (`myClass`) exists in the CSS module file.

## **Supabase Issues** ☁️

* **Issue:** Row-Level Security (RLS) blocking data access (getting empty arrays or `null` when data exists). 🔐
    * **Solution 1:** Verify your RLS policies in the Supabase dashboard (Authentication -> Policies) are **enabled** for the relevant tables (`select`, `insert`, `update`, `delete`).
    * **Solution 2:** Ensure the policies correctly check the user's ID (`auth.uid()`) against the appropriate column (e.g., `user_id`) in the table using a `USING` expression for SELECT and potentially `WITH CHECK` for INSERT/UPDATE.
    * **Solution 3:** Check the Supabase logs (Database -> Logs or query logs in the SQL Editor) for detailed SQL errors related to RLS policy violations.
    * **Solution 4:** Temporarily disable RLS for testing (use with caution!) via the Supabase dashboard toggle to confirm if it's the source of the problem. **Remember to re-enable it.**

* **Issue:** Edge Function errors (check function logs in Supabase dashboard: Edge Functions -> Select function -> Logs).
    * **Solution 1:** Ensure proper authentication/authorization checks are performed within the function (e.g., verifying JWT).
    * **Solution 2:** Check for runtime errors in the Deno environment (e.g., incorrect imports, missing `await`, invalid JSON parsing).
    * **Solution 3:** Verify the request payload sent from the client matches what the Edge Function expects (check types and structure). Log the incoming request body in the function for debugging.

## **Debugging Tips** 🐞

* **Browser Developer Tools (`F12`):** Your best friend!
    * **Console:** Check for JavaScript errors and log messages (`console.log`). Use `console.table()` for arrays/objects.
    * **Network:** Inspect API requests to Edge Functions (check status codes 2xx/4xx/5xx, request/response payloads, headers).
    * **Elements:** Inspect the rendered HTML and applied CSS styles. Check for CSS specificity issues.
    * **Application:** Inspect local storage, session storage, cookies (e.g., Supabase auth token).
* **Supabase Dashboard Logs:**
    * Database -> Logs
    * Edge Functions -> Select function -> Logs
* **SvelteKit Error Pages:** Utilize SvelteKit's error pages (`+error.svelte`) for handling server-side and client-side errors gracefully. Add logging within these pages to capture error details.
* **Strategic Logging:** Add `console.log` statements strategically in both frontend Svelte components (`<script>`) and backend Supabase Edge Functions to trace data flow and variable values. Remove excessive logs before committing.

*(Add more sections and specific errors/solutions as needed as the project evolves!)*