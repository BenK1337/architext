<script lang="ts">
  import Sidebar from '$lib/components/Sidebar/Sidebar.svelte';
  import TopBar from '$lib/components/TopBar/TopBar.svelte';
  import MainPrompt from '$lib/components/MainPrompt/MainPrompt.svelte';
  import RunSettings from '$lib/components/RunSettings/RunSettings.svelte';
  import ProfileMenu from '$lib/components/ProfileMenu/ProfileMenu.svelte';
  import { supabase } from '$lib/supabaseClient';
import type { Provider } from '@supabase/supabase-js';
  import { onMount } from 'svelte';
  // TODO: Type user with Supabase types (e.g. User | null)
  let user: any = null;
  let loading = false;

  // Check auth state on mount
  onMount(async () => {
    const { data: { user: supaUser } } = await supabase.auth.getUser();
    user = supaUser;
  });

  async function loginWithProvider(provider: Provider) {
    loading = true;
    const { error } = await supabase.auth.signInWithOAuth({ provider });
    if (error) {
      // TODO: Show error notification
      console.error(error);
    }
    loading = false;
  }

  async function loginWithPasskey() {
    loading = true;
    // TODO: Implement Passkey login flow with Supabase
    loading = false;
  }

  async function handleLogout() {
    await supabase.auth.signOut();
    user = null;
  }
</script>

<div class="container">
  <Sidebar />
  <div class="main-column">
    <main class="main-area">
      <MainPrompt onRun={(prompt) => { /* TODO: handle run action */ }} />
    </main>
  </div>
  <aside class="right-sidebar">
    <RunSettings />
    {#if $user}
      <ProfileMenu {user} onLogout={handleLogout} />
    {/if}
  </aside>
</div>

<style module>
.container {
  display: flex;
  height: 100vh;
  background: var(--color-surface);
}
.main-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-width: 0;
}
.main-area {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem 4rem;
  background: var(--color-surface);
}
.right-sidebar {
  width: 300px;
  background: var(--color-surface-alt);
  border-left: 1px solid var(--color-border);
  box-shadow: var(--shadow-xs);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 2rem 1rem;
}
</style>
