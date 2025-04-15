<script lang="ts">
  import { fade } from 'svelte/transition';
  import styles from './ActivityFeed.module.css';
  export let activities = [
    { text: 'You created Research Summarizer', time: '2h ago' },
    { text: 'Unit Test Generator updated', time: '1d ago' },
    { text: 'New member joined Docker Script', time: '3d ago' }
  ];
</script>

<section class={styles['activity-feed']} in:fade={{ duration: 350 }}>
  <h3>Activity Feed</h3>
  <ul>
    {#each activities as activity}
      <li>
        <span class={styles['activity-text']}>{activity.text}</span>
        <span class={styles['activity-time']}>{activity.time}</span>
      </li>
    {/each}
  </ul>
</section>

