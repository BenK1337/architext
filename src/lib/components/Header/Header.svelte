<script lang="ts">
  // TODO: Add props for title, actions, navigation, etc.
export let title: string;

  import styles from './Header.module.css';
</script>

<header class={styles.header}>
  <span>{title}</span>
  <slot />
</header>

<style module lang="css">
@import '../../styles/theme.css';
.header {
  display: flex;
  align-items: center;
  height: 3.5rem;
  padding: 0 var(--space-6);
  background: var(--color-surface);
  border-bottom: 1px solid var(--color-border);
  box-shadow: var(--shadow-xs);
  z-index: 10;
}
</style>
