<script lang="ts">
// Import global CSS for theme and base styles
import '../lib/styles/global.css';
import TopBar from '$lib/components/TopBar/TopBar.svelte';
import Sidebar from '$lib/components/Sidebar/Sidebar.svelte';
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
<div class="app-shell">
  <Sidebar />
  <div class="app-main-area">
    <header class="app-header">
      <TopBar {user} onLogout={handleLogout} />
    </header>
    <main class="app-main-content">
      <slot />
    </main>
  </div>
</div>
<style>
.app-shell {
  display: flex;
  height: 100vh;
  background: var(--color-background);
  font-family: var(--font-sans);
  min-width: 0;
}

.app-main-area {
  flex: 1 1 0%;
  display: flex;
  flex-direction: column;
  min-width: 0;
  height: 100vh;
  overflow: auto;
}
.app-header {
  position: sticky;
  top: 0;
  z-index: 10;
  background: var(--color-surface);
  box-shadow: var(--shadow-xs);
  height: 3.5rem;
  display: flex;
  align-items: center;
  padding: 0 2rem;
}
.app-main-content {
  flex: 1 1 auto;
  overflow-y: auto;
  background: var(--color-background);
  padding: 2.5rem 0;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 0;
}



</style>
