<script lang="ts">
  import type { PageData } from './$types';
  import ReportDisplay from '$lib/components/ReportDisplay.svelte';

  export let data: PageData;
</script>

<svelte:head>
  <title>Scan Results - Charity Compliance Checker</title>
</svelte:head>

{#if data.report}
  <ReportDisplay report={data.report} />
{:else}
  <div class="error-state">
    <h2>Unable to load report</h2>
    <p>Please try again or contact support if the issue persists.</p>
    <a href="/" class="button">Go Home</a>
  </div>
{/if}

<style>
  .error-state {
    text-align: center;
    padding: var(--spacing-xxl);
    max-width: 600px;
    margin: 0 auto;
  }

  .error-state h2 {
    color: var(--status-threat);
    margin-bottom: var(--spacing-md);
  }

  .error-state p {
    margin-bottom: var(--spacing-lg);
  }
</style>
