<script lang="ts">
  import ScanInputForm from '$lib/components/ScanInputForm.svelte';
</script>

<svelte:head>
  <title>Charity Compliance Checker</title>
  <meta name="description" content="Automated compliance scanning for charity websites - check GDPR, security, and policy compliance." />
</svelte:head>

<div class="hero">
  <h1>Charity Compliance Checker</h1>
  <p class="tagline">
    Automated compliance scanning for your charity website. Check GDPR, security policies, and more in seconds.
  </p>
</div>

<div class="form-container">
  <ScanInputForm />
</div>

<div class="features">
  <div class="feature">
    <div class="feature-icon">🔒</div>
    <h3>Security Check</h3>
    <p>Verify SSL certificates and HTTPS implementation</p>
  </div>

  <div class="feature">
    <div class="feature-icon">📋</div>
    <h3>Policy Detection</h3>
    <p>Find Privacy, Cookie, and Safeguarding policies</p>
  </div>

  <div class="feature">
    <div class="feature-icon">⚖️</div>
    <h3>GDPR Compliance</h3>
    <p>Check DSAR processes and data processor disclosures</p>
  </div>

  <div class="feature">
    <div class="feature-icon">💳</div>
    <h3>Payment Security</h3>
    <p>Verify PCI DSS compliance for payment processing</p>
  </div>
</div>

<style>
  .hero {
    text-align: center;
    padding: var(--spacing-xxl) 0;
    max-width: 800px;
    margin: 0 auto;
  }

  .hero h1 {
    font-size: 3.5rem;
    margin-bottom: var(--spacing-lg);
    background: linear-gradient(135deg, var(--color-text-primary) 0%, var(--color-accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .tagline {
    font-size: 1.25rem;
    color: var(--color-text-secondary);
    line-height: 1.6;
  }

  .form-container {
    margin: var(--spacing-xxl) 0;
  }

  .features {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-lg);
    margin-top: var(--spacing-xxl);
    padding-top: var(--spacing-xxl);
    border-top: 1px solid var(--color-border);
  }

  .feature {
    text-align: center;
    padding: var(--spacing-lg);
    background-color: var(--color-bg-secondary);
    border-radius: var(--border-radius);
    transition: var(--transition-fast);
  }

  .feature:hover {
    transform: translateY(-4px);
    box-shadow: var(--card-shadow);
  }

  .feature-icon {
    font-size: 3rem;
    margin-bottom: var(--spacing-md);
  }

  .feature h3 {
    font-size: 1.125rem;
    margin-bottom: var(--spacing-sm);
    color: var(--color-text-primary);
  }

  .feature p {
    font-size: 0.875rem;
    color: var(--color-text-secondary);
    margin: 0;
  }

  @media (max-width: 768px) {
    .hero h1 {
      font-size: 2.5rem;
    }

    .features {
      grid-template-columns: 1fr;
    }
  }
</style>
