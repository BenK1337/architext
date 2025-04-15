<script lang="ts">
// TODO: Add props for task, checked, onToggle, etc.
export let checked: boolean = false;
</script>

<div class={styles.taskItem}>
  <input type="checkbox" bind:checked class={styles.checkbox} />
  <span class={styles.label}><slot /></span>
</div>

<style module lang="css">
@import '../../styles/theme.css';
.taskItem {
  display: flex;
  align-items: center;
  padding: var(--space-2) var(--space-3);
  background: var(--color-surface);
  border-radius: var(--border-radius-sm);
  box-shadow: var(--shadow-xs);
  margin-bottom: var(--space-2);
  transition: background var(--transition-fast);
}
.checkbox {
  margin-right: var(--space-3);
  accent-color: var(--color-primary);
  width: 1.2em;
  height: 1.2em;
}
.label {
  flex: 1;
  color: var(--color-on-surface);
}
.taskItem:hover {
  background: var(--color-surface-alt);
}
</style>
