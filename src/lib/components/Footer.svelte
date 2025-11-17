<script lang="ts">
  const currentYear = new Date().getFullYear();
</script>

<footer>
  <div class="container">
    <p class="copyright">&copy; {currentYear} Charity Compliance Checker. All rights reserved.</p>
    <p class="disclaimer">
      This tool provides automated guidance only. Always consult with a qualified legal professional for compliance advice.
    </p>
  </div>
</footer>

<style>
  footer {
    background: rgba(255, 255, 255, 0.02);
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    padding: 40px 2rem;
    margin-top: 120px;
    position: relative;
    z-index: 1;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    text-align: center;
  }

  .copyright {
    font-family: 'Inter', sans-serif;
    font-size: 14px;
    font-weight: 400;
    color: #ffffff;
    margin-bottom: 8px;
  }

  .disclaimer {
    font-family: 'Inter', sans-serif;
    font-size: 12px;
    font-weight: 400;
    color: #6b7280;
    font-style: italic;
    max-width: 600px;
    margin: 0 auto;
  }
</style>
