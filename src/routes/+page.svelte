<script lang="ts">
  import Header from '../lib/components/Header/Header.svelte';
  import Sidebar from '../lib/components/Sidebar/Sidebar.svelte';
</script>

<div>
  <Header slot="header" title="Architext AI" />
  <Sidebar slot="sidebar" />
  <div class="landing-container">
    <section class="landing-section">
      <h1>Welcome to Architext AI</h1>
      <p>This is your MVP shell. Use the sidebar to navigate and the header for actions.</p>
    </section>
  </div>
</div>

<style>
.landing-container {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 80vh;
  width: 100vw;
  background: var(--color-background);
}
.landing-section {
  background: var(--color-surface);
  padding: 2.5rem 3rem;
  border-radius: 1.2rem;
  box-shadow: var(--shadow-md);
  text-align: center;
  max-width: 440px;
  width: 100%;
}
.landing-section h1 {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1.2rem;
}
.landing-section p {
  font-size: 1.1rem;
  color: var(--color-on-surface-muted);
}
</style>
