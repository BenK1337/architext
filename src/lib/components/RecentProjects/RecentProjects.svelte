<script lang="ts">
  import { fade } from 'svelte/transition';
  import styles from './RecentProjects.module.css';
  export let projects = [
    { name: 'Research Summarizer', updated: '2h ago' },
    { name: 'Unit Test Generator', updated: '1d ago' },
    { name: 'Docker Script', updated: '3d ago' }
  ];
</script>

<section class={styles['recent-projects']} in:fade={{ duration: 350 }}>
  <h3>Recent Projects</h3>
  <ul>
    {#each projects as project}
      <li>
        <span class={styles['project-name']}>{project.name}</span>
        <span class={styles.updated}>{project.updated}</span>
      </li>
    {/each}
  </ul>
</section>
