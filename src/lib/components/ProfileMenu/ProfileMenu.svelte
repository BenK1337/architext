<script lang="ts">
  import { type Writable } from 'svelte/store';
export let user: Writable<{ avatar_url?: string; email?: string; provider?: string } | null>;

  export let onLogout: () => void = () => {};
</script>

{#if $user}
  <div class="profile-menu">
    <img class="avatar" src={$user.avatar_url || '/default-avatar.png'} alt="User avatar" />
    <div class="profile-info">
      <div class="profile-name">{$user.email}</div>
      <div class="profile-provider">{$user.provider}</div>
    </div>
    <button class="switch-account">Konto wechseln</button>
    <button class="logout" on:click={onLogout}>Abmelden</button>
  </div>
{/if}

<style module>
.profile-menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: 1rem;
  box-shadow: var(--shadow-lg);
  min-width: 220px;
  z-index: 100;
  padding: 1rem;
}
.avatar {
  width: 2.2rem;
  height: 2.2rem;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 0.8rem;
  border: 2px solid var(--color-border);
}
.profile-info {
  text-align: center;
  margin-bottom: 0.8rem;
}
.profile-name {
  font-weight: 600;
  font-size: 1.05rem;
}
.profile-provider {
  font-size: 0.95rem;
  color: var(--color-text-secondary);
}
.switch-account,
.logout {
  width: 100%;
  margin-top: 0.4rem;
  padding: 0.5rem 0;
  border: none;
  border-radius: 0.7rem;
  background: var(--color-surface-alt);
  color: var(--color-text-secondary);
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.2s, color 0.2s;
}
.switch-account:hover,
.logout:hover {
  background: var(--color-primary-faint);
  color: var(--color-primary);
}
</style>
