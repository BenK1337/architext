<script lang="ts">
import WorkspaceOverview from '$lib/components/WorkspaceOverview/WorkspaceOverview.svelte';
import RecentProjects from '$lib/components/RecentProjects/RecentProjects.svelte';
import QuickActions from '$lib/components/QuickActions/QuickActions.svelte';
import ActivityFeed from '$lib/components/ActivityFeed/ActivityFeed.svelte';
import WelcomeBanner from '$lib/components/WelcomeBanner/WelcomeBanner.svelte';
</script>

<div>
  <div class="dashboard-container">
    <div class="dashboard-main">
      <WorkspaceOverview />
      <WelcomeBanner />
      <QuickActions />
      <RecentProjects />
    </div>
    <div class="dashboard-side">
      <ActivityFeed />
    </div>
  </div>
</div>

<style>
.dashboard-container {
  display: flex;
  gap: 2.5rem;
  padding: 2.5rem 3rem;
  max-width: 1200px;
  margin: 0 auto;
}
.dashboard-main {
  flex: 2;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 0;
}
.dashboard-side {
  flex: 1;
  min-width: 280px;
  max-width: 350px;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
@media (max-width: 900px) {
  .dashboard-container {
    flex-direction: column;
    padding: 1rem;
    gap: 1.5rem;
  }
  .dashboard-side {
    max-width: none;
    min-width: 0;
  }
}
</style>
