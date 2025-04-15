<script lang="ts">
  // Placeholder for run/settings panel props and logic
</script>

<aside class="run-settings">
  <div class="panel-title">Run settings</div>
  <div class="setting-row">
    <label for="temperature">Temperature</label>
    <input type="range" id="temperature" min="0" max="2" step="0.01" value="1" />
    <span class="value">1</span>
  </div>
  <div class="setting-row">
    <label>Tools</label>
    <div class="toggle-group">
      <label><input type="checkbox" /> Structured output</label>
      <label><input type="checkbox" /> Code execution</label>
      <label><input type="checkbox" /> Function calling</label>
      <label><input type="checkbox" /> Grounding with Google Search</label>
    </div>
  </div>
  <div class="setting-row">
    <label>Advanced settings</label>
    <div class="advanced-group">
      <label>Safety settings <input type="checkbox" /></label>
      <label>Output length <input type="number" min="1" max="65536" value="65536" /></label>
      <label>Top P <input type="range" min="0" max="1" step="0.01" value="0.95" /></label>
    </div>
  </div>
</aside>

<style module>
.run-settings {
  width: 100%;
  background: var(--color-surface-alt);
  border-left: 1px solid var(--color-border);
  box-shadow: var(--shadow-xs);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 2rem 1rem;
  border-radius: 1.5rem;
}
.panel-title {
  font-weight: 700;
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
}
.setting-row {
  margin-bottom: 1.5rem;
  width: 100%;
}
.setting-row label {
  font-size: 1rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
  display: block;
}
.toggle-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-left: 1rem;
}
.advanced-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-left: 1rem;
}
.value {
  margin-left: 0.7rem;
  font-size: 0.96rem;
  color: var(--color-text-secondary);
}
</style>
