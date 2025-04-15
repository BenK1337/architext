<script lang="ts">
// Import global CSS for theme and base styles
import '../lib/styles/global.css';
import TopBar from '$lib/components/TopBar/TopBar.svelte';
import { supabase } from '$lib/supabaseClient';
import { onMount } from 'svelte';
import { writable } from 'svelte/store';

// User state for session
const user = writable<{ avatar_url?: string; email?: string; provider?: string } | null>(null);

onMount(async () => {
  const { data: { user: supaUser } } = await supabase.auth.getUser();
  if (supaUser) {
    user.set({
      avatar_url: supaUser.user_metadata?.avatar_url,
      email: supaUser.email,
      provider: supaUser.app_metadata?.provider
    });
  }
  // Listen for auth state changes
  supabase.auth.onAuthStateChange((_event, session) => {
    if (session?.user) {
      user.set({
        avatar_url: session.user.user_metadata?.avatar_url,
        email: session.user.email,
        provider: session.user.app_metadata?.provider
      });
    } else {
      user.set(null);
    }
  });
});

function handleLogout() {
  supabase.auth.signOut();
  user.set(null);
}

</script>

<!-- Main App Layout -->
<header class="app-header">
  <TopBar {user} onLogout={handleLogout} />
  <slot name="header" />
</header>
<div class="app-shell">
  <div class="app-body">
    <aside class="app-sidebar">
      <slot name="sidebar" />
    </aside>
    <main class="app-main">
      <slot />
    </main>
  </div>
</div>

<style>
.app-shell {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: var(--color-background);
}
.app-header {
  width: 100%;
  position: sticky;
  top: 0;
  z-index: 10;
  background: var(--color-surface);
  box-shadow: var(--shadow-xs);
}
.app-body {
  flex: 1 1 auto;
  display: flex;
  min-height: 0;
}
.app-sidebar {
  width: 240px;
  min-width: 180px;
  max-width: 320px;
  background: var(--color-surface);
  border-right: 1px solid var(--color-border);
  min-height: 0;
  overflow-y: auto;
}
.app-main {
  flex: 1 1 auto;
  min-width: 0;
  min-height: 0;
  padding: var(--space-6) var(--space-8);
  background: var(--color-background);
  overflow-y: auto;
}
@media (max-width: 900px) {
  .app-body {
    flex-direction: column;
  }
  .app-sidebar {
    width: 100%;
    max-width: none;
    border-right: none;
    border-bottom: 1px solid var(--color-border);
  }
}
</style>
