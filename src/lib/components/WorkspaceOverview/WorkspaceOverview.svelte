<script lang="ts">
  import { fade } from 'svelte/transition';
  import styles from './WorkspaceOverview.module.css';
  export let workspace = { name: 'Demo Workspace', members: 3 };
</script>

<section class={styles['workspace-overview']} in:fade={{ duration: 350 }}>
  <h2>{workspace.name}</h2>
  <div class={styles.members}>{workspace.members} members</div>
  <button class={styles['settings-btn']}>⚙️ Settings</button>
</section>
