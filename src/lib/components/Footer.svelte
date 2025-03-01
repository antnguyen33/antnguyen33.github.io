<script>
  import { footerText } from "$lib/constants";
  const date = new Date();
  const dateString = date.toDateString()
</script>

<p>Updated {dateString}. <a href="https://github.com/sharu725/yuyutsu">{footerText}</a></p>

<style>
  p {
    color: #ddd;
    font-size: 0.9rem;
  }
  
  p a {
    color: #ddd
  }
</style>
