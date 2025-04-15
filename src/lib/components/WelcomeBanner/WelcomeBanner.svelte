<script lang="ts">
  import { fade } from 'svelte/transition';
  import styles from './WelcomeBanner.module.css';
</script>

<section class={styles['welcome-banner']} in:fade={{ duration: 350 }}>
  <h2>Welcome to Architext AI!</h2>
  <p>Start by creating a new project or exploring templates. Your workspace is ready for action!</p>
</section>
