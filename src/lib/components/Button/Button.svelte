<script lang="ts">
// TODO: Add props for variant, size, loading, disabled, icon, etc.
// Use design tokens from theme.css for styling
export let type: 'button' | 'submit' | 'reset' = 'button';
export let disabled: boolean = false;
</script>

<button type={type} disabled={disabled} class={styles.button}>
  <slot />
</button>

<style module lang="css">
@import '../../styles/theme.css';
.button {
  background: var(--color-primary);
  color: var(--color-on-primary);
  font-family: var(--font-sans);
  font-size: var(--font-size-md);
  font-weight: var(--font-weight-medium);
  padding: var(--space-2) var(--space-4);
  border-radius: var(--border-radius-md);
  border: none;
  box-shadow: var(--shadow-xs);
  transition: background var(--transition-fast), box-shadow var(--transition-fast), transform var(--transition-fast);
  cursor: pointer;
  outline: none;
}
.button:hover:not(:disabled) {
  background: var(--color-primary-hover);
  box-shadow: var(--shadow-sm);
}
.button:active:not(:disabled) {
  background: var(--color-primary-active);
  transform: scale(0.98);
}
.button:disabled {
  background: var(--color-disabled);
  color: var(--color-on-surface-muted);
  cursor: not-allowed;
}
</style>
