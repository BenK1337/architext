<script lang="ts">
  // TODO: Add props for navigation items, collapsed state, etc.
  import styles from './Sidebar.module.css';
</script>

<aside class={styles.sidebar}>
  <div class={styles.logoSection}>
    <img src="/logo.svg" alt="Architext Logo" class={styles.logo} />
    <span class={styles.brand}>Architext AI</span>
  </div>
  <nav class={styles.navSection} aria-label="Main Navigation">
    <div class={styles.navList}>
      <button class={styles.navItem} aria-label="Workspace">
        <span class={styles.icon}><svg width="20" height="20"><rect x="3" y="7" width="14" height="10" rx="3" fill="none" stroke="currentColor" stroke-width="2"/></svg></span>
        <span class={styles.navText}>Workspace</span>
      </button>
      <button class={styles.navItem} aria-label="Templates">
        <span class={styles.icon}><svg width="20" height="20"><rect x="5" y="5" width="10" height="10" rx="2" fill="none" stroke="currentColor" stroke-width="2"/></svg></span>
        <span class={styles.navText}>Templates</span>
      </button>
      <button class={styles.navItem} aria-label="My Projects">
        <span class={styles.icon}><svg width="20" height="20"><circle cx="10" cy="10" r="7" fill="none" stroke="currentColor" stroke-width="2"/></svg></span>
        <span class={styles.navText}>My Projects</span>
      </button>
      <button class={styles.navItem} aria-label="Explore">
        <span class={styles.icon}><svg width="20" height="20"><path d="M10 2 L18 18 L2 18 Z" fill="none" stroke="currentColor" stroke-width="2"/></svg></span>
        <span class={styles.navText}>Explore</span>
      </button>
    </div>
    <div class={styles.historySection}>
      <div class={styles.historyTitle}>History</div>
      <div class={styles.historyList}>
        <button class={styles.historyItem}>Research Summarizer Session</button>
        <button class={styles.historyItem}>Python Unit Test Generator</button>
        <button class={styles.historyItem}>Docker Setup Script Builder</button>
        <button class={styles.historyItem}>Presentation Slide Creator</button>
      </div>
    </div>
  </nav>
  <footer class={styles.footerSection}>
    <a href="/docs" class={styles.footerLink}>Docs</a>
    <a href="/support" class={styles.footerLink}>Support</a>
    <a href="/terms" class={styles.footerLink}>Terms</a>
  </footer>
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
