<script lang="ts">
  import { fade } from 'svelte/transition';
  import styles from './QuickActions.module.css';
</script>

<section class={styles['quick-actions']} in:fade={{ duration: 350 }}>
  <button class={styles['new-project']}>+ New Project</button>
  <button class={styles.import}>Import</button>
  <button class={styles.template}>Start from Template</button>
</section>

