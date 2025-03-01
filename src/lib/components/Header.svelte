<script>
  import { base } from "$app/paths";
  import { siteTitle } from "$lib/constants";
</script>

<div class="header-container">
  <header class="container">
    <a data-sveltekit-prefetch href="{base}/"><h1>{siteTitle}</h1></a>
  </header>
</div>

<style>
  .header-container {
    border-bottom: 1px solid var(--bg-light);
    background-color: var(--headers-color);
  }
  header h1 {
    font-size: 2rem;
    margin: 0;
    font-weight: 600;
    text-align: center;
    color: var(--text-light);
  }

  header a {
    text-decoration: none;
  }

  @media screen and (max-width: 800px) {
    header h1 {
      text-align: center;
      margin: 0;
    }
  }
</style>
