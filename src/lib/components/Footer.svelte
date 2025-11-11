<script lang="ts">
  const currentYear = new Date().getFullYear();
</script>

<footer>
  <div class="container">
    <p>&copy; {currentYear} Charity Compliance Checker. All rights reserved.</p>
    <p class="disclaimer">
      This tool provides automated guidance only. Always consult with a qualified legal professional for compliance advice.
    </p>
  </div>
</footer>

<style>
  footer {
    background-color: var(--color-bg-secondary);
    border-top: 1px solid var(--color-border);
    padding: var(--spacing-xl) 0;
    margin-top: var(--spacing-xxl);
  }

  .container {
    max-width: var(--container-width);
    margin: 0 auto;
    padding: 0 var(--spacing-md);
    text-align: center;
  }

  p {
    font-size: 0.875rem;
    color: var(--color-text-secondary);
    margin-bottom: var(--spacing-sm);
  }

  .disclaimer {
    font-size: 0.75rem;
    color: var(--color-text-secondary);
    opacity: 0.7;
    font-style: italic;
  }
</style>
