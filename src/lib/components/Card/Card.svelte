<script lang="ts">
  // TODO: Add props for elevation, padding, clickable, etc.
  import styles from './Card.module.css';
</script>

<div class={styles.card}>
  <slot />
</div>

<style module lang="css">
@import '../../styles/theme.css';
.card {
  background: var(--color-surface);
  color: var(--color-on-surface);
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-sm);
  padding: var(--space-4);
  transition: box-shadow var(--transition-fast), transform var(--transition-fast);
}
.card:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-2px) scale(1.01);
}
</style>
