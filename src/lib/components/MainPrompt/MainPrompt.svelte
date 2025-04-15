<script lang="ts">
  // Placeholder for prompt input, suggestion chips, and Run button/dropdown
  export let onRun: (prompt: string) => void = () => {};
  let prompt = '';
  const suggestions = [
    'Summarize this research paper.',
    'Generate a project README.',
    'Draft a privacy policy.',
    'Create a presentation outline.'
  ];
</script>

<div class="main-prompt">
  <h1>Welcome to Architext AI</h1>
  <div class="prompt-row">
    <input
      type="text"
      bind:value={prompt}
      placeholder="Type something or pick one from prompt gallery"
      on:keydown={(e) => e.key === 'Enter' && onRun(prompt)}
    />
    <button class="run-btn" on:click={() => onRun(prompt)}>Run</button>
    <!-- Dropdown for Run button (file, audio, camera, etc.) will be implemented -->
  </div>
  <div class="suggestion-chips">
    {#each suggestions as suggestion}
      <button class="chip" on:click={() => onRun(suggestion)}>{suggestion}</button>
    {/each}
  </div>
</div>

<style module>
.main-prompt {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding: 3rem 0 2rem 0;
}
.prompt-row {
  display: flex;
  align-items: center;
  margin: 2rem 0 1rem 0;
  gap: 1rem;
  width: 100%;
  max-width: 600px;
}
input[type="text"] {
  flex: 1;
  padding: 0.75rem 1rem;
  font-size: 1.1rem;
  border: 1px solid var(--color-border);
  border-radius: 2rem;
  outline: none;
  background: var(--color-surface-alt);
}
.run-btn {
  padding: 0.75rem 1.5rem;
  border-radius: 2rem;
  background: var(--color-primary);
  color: #fff;
  border: none;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: var(--shadow-xs);
  transition: background 0.2s;
}
.run-btn:hover {
  background: var(--color-primary-hover);
}
.suggestion-chips {
  display: flex;
  gap: 0.75rem;
  margin-bottom: 2rem;
}
.chip {
  padding: 0.5rem 1.25rem;
  border-radius: 2rem;
  background: var(--color-surface-alt);
  border: 1px solid var(--color-border);
  font-size: 0.95rem;
  color: var(--color-text-secondary);
  cursor: pointer;
  transition: background 0.2s, border 0.2s;
}
.chip:hover {
  background: var(--color-primary-faint);
  border-color: var(--color-primary);
  color: var(--color-primary);
}
</style>
