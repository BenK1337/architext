<script lang="ts">
// TODO: Add props for navigation items, collapsed state, etc.
</script>

<aside class={styles.sidebar}>
  <slot />
</aside>

<style module lang="css">
@import '../../styles/theme.css';
.sidebar {
  width: 16rem;
  min-width: 12rem;
  background: var(--color-surface-alt);
  border-right: 1px solid var(--color-border);
  height: 100vh;
  display: flex;
  flex-direction: column;
  box-shadow: var(--shadow-xs);
  transition: width var(--transition-medium);
}
</style>
