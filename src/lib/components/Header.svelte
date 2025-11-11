<script lang="ts">
  // No props needed for this simple header
</script>

<header>
  <div class="container">
    <a href="/" class="logo">
      <h1>Charity Compliance Checker</h1>
    </a>
    <nav>
      <a href="/">Home</a>
    </nav>
  </div>
</header>

<style>
  header {
    background-color: var(--color-bg-primary);
    border-bottom: 1px solid var(--color-border);
    padding: var(--spacing-md) 0;
    position: sticky;
    top: 0;
    z-index: 100;
    backdrop-filter: blur(10px);
    background-color: rgba(255, 255, 255, 0.8);
  }

  .container {
    max-width: var(--container-width);
    margin: 0 auto;
    padding: 0 var(--spacing-md);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .logo h1 {
    font-size: 1.25rem;
    font-weight: 600;
    color: var(--color-text-primary);
    margin: 0;
    transition: var(--transition-fast);
  }

  .logo:hover h1 {
    color: var(--color-accent);
  }

  nav {
    display: flex;
    gap: var(--spacing-lg);
  }

  nav a {
    font-size: 1rem;
    font-weight: 500;
    color: var(--color-text-secondary);
    transition: var(--transition-fast);
  }

  nav a:hover {
    color: var(--color-accent);
  }
</style>
