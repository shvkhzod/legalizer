<script lang="ts">
  import type { ComplianceReport } from '$lib/utils/types';
  import ReportCard from './ReportCard.svelte';

  export let report: ComplianceReport;

  function formatDate(isoString: string): string {
    const date = new Date(isoString);
    return date.toLocaleDateString('en-GB', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      hour: '2-digit',
      minute: '2-digit'
    });
  }

  function getOverallStatusColor(status: string): string {
    switch (status) {
      case 'Compliant':
        return 'var(--status-good)';
      case 'Warning':
        return 'var(--status-warning)';
      case 'Non-Compliant':
        return 'var(--status-threat)';
      default:
        return 'var(--color-text-secondary)';
    }
  }

  function getScoreColor(score: number): string {
    if (score > 85) return 'var(--status-good)';
    if (score > 60) return 'var(--status-warning)';
    return 'var(--status-threat)';
  }
</script>

<div class="report-display">
  <!-- Overall Summary -->
  <div class="report-header">
    <div class="header-content">
      <h1>Compliance Report</h1>
      <p class="scan-info">
        <strong>Scanned URL:</strong> <a href={report.scannedUrl} target="_blank" rel="noopener noreferrer">{report.scannedUrl}</a>
      </p>
      <p class="scan-info">
        <strong>Scan Date:</strong> {formatDate(report.scanDate)}
      </p>
    </div>

    <div class="score-container">
      <div class="score-circle" style="border-color: {getScoreColor(report.overallScore)};">
        <span class="score-number">{report.overallScore}</span>
        <span class="score-label">/ 100</span>
      </div>
      <div class="overall-status" style="color: {getOverallStatusColor(report.overallStatus)};">
        {report.overallStatus}
      </div>
    </div>
  </div>

  <!-- Summary Section -->
  {#if report.summary.goodPoints.length > 0 || report.summary.warnings.length > 0 || report.summary.threats.length > 0}
    <div class="summary-section">
      <h2>Executive Summary</h2>

      {#if report.summary.goodPoints.length > 0}
        <div class="summary-box good">
          <h3>✓ Strengths</h3>
          <ul>
            {#each report.summary.goodPoints as point}
              <li>{point}</li>
            {/each}
          </ul>
        </div>
      {/if}

      {#if report.summary.warnings.length > 0}
        <div class="summary-box warning">
          <h3>⚠ Warnings</h3>
          <ul>
            {#each report.summary.warnings as warning}
              <li>{warning}</li>
            {/each}
          </ul>
        </div>
      {/if}

      {#if report.summary.threats.length > 0}
        <div class="summary-box threat">
          <h3>✗ Critical Issues</h3>
          <ul>
            {#each report.summary.threats as threat}
              <li>{threat}</li>
            {/each}
          </ul>
        </div>
      {/if}
    </div>
  {/if}

  <!-- Detailed Checks -->
  <div class="checks-section">
    <h2>Detailed Findings</h2>

    {#if report.checks.security.length > 0}
      <div class="check-category">
        <h3>Security</h3>
        {#each report.checks.security as check}
          <ReportCard {check} />
        {/each}
      </div>
    {/if}

    {#if report.checks.websitePolicies.length > 0}
      <div class="check-category">
        <h3>Website Policies</h3>
        {#each report.checks.websitePolicies as check}
          <ReportCard {check} />
        {/each}
      </div>
    {/if}

    {#if report.checks.marketing.length > 0}
      <div class="check-category">
        <h3>Marketing Compliance</h3>
        {#each report.checks.marketing as check}
          <ReportCard {check} />
        {/each}
      </div>
    {/if}

    {#if report.checks.payments.length > 0}
      <div class="check-category">
        <h3>Payment Processing</h3>
        {#each report.checks.payments as check}
          <ReportCard {check} />
        {/each}
      </div>
    {/if}

    {#if report.checks.memberData.length > 0}
      <div class="check-category">
        <h3>Member Data & Copyright</h3>
        {#each report.checks.memberData as check}
          <ReportCard {check} />
        {/each}
      </div>
    {/if}
  </div>

  <!-- Action Buttons -->
  <div class="action-buttons">
    <a href="/" class="button">Scan Another Website</a>
  </div>
</div>

<style>
  .report-display {
    max-width: 900px;
    margin: 0 auto;
  }

  .report-header {
    background: linear-gradient(135deg, var(--color-bg-secondary) 0%, var(--color-bg-primary) 100%);
    border: 1px solid var(--color-border);
    border-radius: var(--border-radius);
    padding: var(--spacing-xl);
    margin-bottom: var(--spacing-xl);
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: var(--spacing-lg);
  }

  .header-content {
    flex: 1;
  }

  .report-header h1 {
    margin-bottom: var(--spacing-sm);
  }

  .scan-info {
    font-size: 0.875rem;
    color: var(--color-text-secondary);
    margin-bottom: var(--spacing-xs);
  }

  .scan-info a {
    word-break: break-all;
  }

  .score-container {
    text-align: center;
  }

  .score-circle {
    width: 120px;
    height: 120px;
    border: 6px solid;
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-bottom: var(--spacing-sm);
  }

  .score-number {
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--color-text-primary);
    line-height: 1;
  }

  .score-label {
    font-size: 0.875rem;
    color: var(--color-text-secondary);
  }

  .overall-status {
    font-size: 1.25rem;
    font-weight: 600;
  }

  .summary-section {
    margin-bottom: var(--spacing-xl);
  }

  .summary-box {
    border-left: 4px solid;
    padding: var(--spacing-lg);
    margin-bottom: var(--spacing-md);
    border-radius: var(--border-radius);
    background-color: var(--color-bg-secondary);
  }

  .summary-box.good {
    border-color: var(--status-good);
    background-color: rgba(52, 199, 89, 0.05);
  }

  .summary-box.warning {
    border-color: var(--status-warning);
    background-color: rgba(255, 149, 0, 0.05);
  }

  .summary-box.threat {
    border-color: var(--status-threat);
    background-color: rgba(255, 59, 48, 0.05);
  }

  .summary-box h3 {
    margin-top: 0;
    margin-bottom: var(--spacing-sm);
    font-size: 1.125rem;
  }

  .summary-box ul {
    margin: 0;
    padding-left: var(--spacing-lg);
  }

  .summary-box li {
    margin-bottom: var(--spacing-xs);
  }

  .checks-section {
    margin-bottom: var(--spacing-xl);
  }

  .check-category {
    margin-bottom: var(--spacing-xl);
  }

  .check-category > h3 {
    font-size: 1.5rem;
    color: var(--color-text-primary);
    margin-bottom: var(--spacing-md);
    padding-bottom: var(--spacing-sm);
    border-bottom: 2px solid var(--color-border);
  }

  .action-buttons {
    display: flex;
    justify-content: center;
    gap: var(--spacing-md);
    margin-top: var(--spacing-xl);
    padding-top: var(--spacing-xl);
    border-top: 1px solid var(--color-border);
  }

  @media (max-width: 768px) {
    .report-header {
      flex-direction: column;
      text-align: center;
    }

    .score-circle {
      width: 100px;
      height: 100px;
    }

    .score-number {
      font-size: 2rem;
    }
  }
</style>
