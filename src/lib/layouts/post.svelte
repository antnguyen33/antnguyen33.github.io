<script>
  import Seo from "$lib/components/Seo.svelte";
  import Categories from "$lib/components/Categories.svelte";
  import { siteTitle } from "$lib/constants";

  export let data;
  export let title, description, date, categories, edit, image;

  const processImagePath = (imagePath) => {
    return `/src/lib/images/${imagePath}`;
  };

  const processedImage = processImagePath(image);
  
  const seo = {
    title: `${title} | ${siteTitle}`,
    description,
    image: processedImage,
  };

  $: recentPosts = data.posts;
</script>

<Seo {...seo} />

<h1>{title}</h1>
<p class="date">{date}</p>
<Categories {categories} />
<img class="cropped-image" src={processedImage} alt={title} />
<article>
  <slot />
</article>

<style>
  .cropped-image {
  width: 800px; 
  height: 300px; 
  object-fit: cover; 
  object-position: 50% 20%;;
  }
</style>