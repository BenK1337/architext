<script lang="ts">
  // Placeholder for props: user, onLogout, etc.
  import { type Writable } from 'svelte/store';
export let user: Writable<{ avatar_url?: string; email?: string; provider?: string } | null>;

  export let onLogout: () => void = () => {};
</script>

<nav class="topbar">
  <div class="left">
    <span class="studio-title">Studio</span>
    <a href="/dashboard" class="nav-link">Dashboard</a>
    <a href="/docs" class="nav-link">Documentation</a>
  </div>
  <div class="right">
    <button class="get-api-key">Get API key</button>
    <button class="settings-btn" aria-label="Settings">
      <svg width="20" height="20" fill="none" viewBox="0 0 24 24"><path d="M12 15.5A3.5 3.5 0 1 0 12 8.5a3.5 3.5 0 0 0 0 7Z" stroke="currentColor" stroke-width="1.5"/><path d="M19.5 12c0-.563.057-1.11.164-1.635a1.06 1.06 0 0 0-.265-1.01l-1.05-1.05a1.06 1.06 0 0 1-.21-1.175l.5-1.232a1.06 1.06 0 0 0-.4-1.262l-1.2-.693a1.06 1.06 0 0 0-1.313.125l-.975.975a1.06 1.06 0 0 1-1.01.265A7.07 7.07 0 0 0 12 4.5c-.563 0-1.11.057-1.635.164a1.06 1.06 0 0 1-1.01-.265l-1.05-1.05a1.06 1.06 0 0 0-1.175-.21l-1.232.5a1.06 1.06 0 0 0-1.262.4l-.693 1.2a1.06 1.06 0 0 0 .125 1.313l.975.975a1.06 1.06 0 0 1 .265 1.01A7.07 7.07 0 0 0 4.5 12c0 .563.057 1.11.164 1.635a1.06 1.06 0 0 1-.265 1.01l-1.05 1.05a1.06 1.06 0 0 0-.21 1.175l.5 1.232a1.06 1.06 0 0 0 .4 1.262l1.2.693a1.06 1.06 0 0 0 1.313-.125l.975-.975a1.06 1.06 0 0 1 1.01-.265A7.07 7.07 0 0 0 12 19.5c.563 0 1.11-.057 1.635-.164a1.06 1.06 0 0 1 1.01.265l1.05 1.05a1.06 1.06 0 0 0 1.175.21l1.232-.5a1.06 1.06 0 0 0 1.262-.4l.693-1.2a1.06 1.06 0 0 0-.125-1.313l-.975-.975a1.06 1.06 0 0 1-.265-1.01A7.07 7.07 0 0 0 19.5 12Z" stroke="currentColor" stroke-width="1.5"/></svg>
    </button>
    {#if $user}
      <div class="avatar-menu">
        <img class="avatar" src={$user.avatar_url || '/default-avatar.png'} alt="User avatar" />
        <div class="profile-dropdown">
          <div class="profile-info">
            <img class="avatar" src={$user.avatar_url || '/default-avatar.png'} alt="User avatar" />
            <div>
              <div class="profile-name">{$user.email}</div>
              <div class="profile-provider">{$user.provider}</div>
            </div>
          </div>
          <button class="switch-account">Konto wechseln</button>
          <button class="logout" on:click={onLogout}>Abmelden</button>
        </div>
      </div>
    {/if}
  </div>
</nav>

<style module>
.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 3.5rem;
  padding: 0 2rem;
  background: var(--color-surface);
  border-bottom: 1px solid var(--color-border);
  box-shadow: var(--shadow-xs);
  z-index: 10;
}
.left {
  display: flex;
  align-items: center;
  gap: 2rem;
}
.studio-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--color-primary);
}
.nav-link {
  color: var(--color-text-secondary);
  text-decoration: none;
  font-size: 1.05rem;
  margin-right: 1rem;
  transition: color 0.2s;
}
.nav-link:hover {
  color: var(--color-primary);
}
.right {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}
.get-api-key {
  background: var(--color-primary-faint);
  color: var(--color-primary);
  border: none;
  border-radius: 1.5rem;
  padding: 0.5rem 1.2rem;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.2s;
}
.get-api-key:hover {
  background: var(--color-primary-hover);
  color: #fff;
}
.settings-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.3rem;
  border-radius: 50%;
  transition: background 0.2s;
}
.settings-btn:hover {
  background: var(--color-primary-faint);
}
.avatar-menu {
  position: relative;
  display: flex;
  align-items: center;
}
.avatar {
  width: 2.2rem;
  height: 2.2rem;
  border-radius: 50%;
  object-fit: cover;
  cursor: pointer;
  border: 2px solid var(--color-border);
}
.profile-dropdown {
  display: none;
  position: absolute;
  right: 0;
  top: 2.5rem;
  background: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: 1rem;
  box-shadow: var(--shadow-lg);
  min-width: 220px;
  z-index: 100;
  padding: 1rem;
}
.avatar-menu:hover .profile-dropdown,
.avatar-menu:focus-within .profile-dropdown {
  display: block;
}
.profile-info {
  display: flex;
  align-items: center;
  gap: 0.8rem;
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
