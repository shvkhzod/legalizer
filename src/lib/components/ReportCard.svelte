<script lang="ts">
  import type { ComplianceCheck } from '$lib/utils/types';

  export let check: ComplianceCheck;

  function getStatusColor(status: string): string {
    switch (status) {
      case 'Compliant':
        return 'var(--status-good)';
      case 'Warning':
        return 'var(--status-warning)';
      case 'Non-Compliant':
        return 'var(--status-threat)';
      case 'Info':
        return 'var(--status-info)';
      default:
        return 'var(--color-text-secondary)';
    }
  }

  function getStatusIcon(status: string): string {
    switch (status) {
      case 'Compliant':
        return '✓';
      case 'Warning':
        return '⚠';
      case 'Non-Compliant':
        return '✗';
      case 'Info':
        return 'ℹ';
      default:
        return '';
    }
  }
</script>

<div class="report-card">
  <div class="card-header">
    <div class="status-badge" style="background-color: {getStatusColor(check.status)};">
      <span class="status-icon">{getStatusIcon(check.status)}</span>
      <span class="status-text">{check.status}</span>
    </div>
    <h3>{check.title}</h3>
  </div>

  <div class="card-body">
    <p class="summary">{check.summary}</p>
    <div class="recommendation">
      <strong>Recommendation:</strong>
      <p>{check.recommendation}</p>
    </div>
  </div>
</div>

<style>
  .report-card {
    background-color: var(--color-bg-primary);
    border: 1px solid var(--color-border);
    border-radius: var(--border-radius);
    padding: var(--spacing-lg);
    margin-bottom: var(--spacing-md);
    box-shadow: var(--card-shadow);
    transition: var(--transition-fast);
  }

  .report-card:hover {
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
  }

  .card-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    margin-bottom: var(--spacing-md);
  }

  .status-badge {
    display: flex;
    align-items: center;
    gap: var(--spacing-xs);
    padding: var(--spacing-xs) var(--spacing-sm);
    border-radius: calc(var(--border-radius) / 2);
    color: white;
    font-size: 0.875rem;
    font-weight: 600;
    white-space: nowrap;
  }

  .status-icon {
    font-size: 1rem;
  }

  .card-header h3 {
    margin: 0;
    font-size: 1.25rem;
    color: var(--color-text-primary);
  }

  .card-body {
    margin-top: var(--spacing-md);
  }

  .summary {
    font-size: 1rem;
    color: var(--color-text-secondary);
    margin-bottom: var(--spacing-md);
  }

  .recommendation {
    background-color: var(--color-bg-secondary);
    padding: var(--spacing-md);
    border-radius: calc(var(--border-radius) / 2);
    border-left: 3px solid var(--color-accent);
  }

  .recommendation strong {
    color: var(--color-text-primary);
    font-size: 0.875rem;
    display: block;
    margin-bottom: var(--spacing-xs);
  }

  .recommendation p {
    margin: 0;
    font-size: 0.875rem;
    color: var(--color-text-secondary);
  }
</style>
