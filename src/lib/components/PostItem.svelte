<script>
  import Categories from "$lib/components/Categories.svelte";
  export let post;
  $: ({ title, description, slug, categories, image } = post);
  const processImagePath = (imagePath) => {
    return `/src/lib/images/${imagePath}`;
  };
  const processedImage = processImagePath(post.image);
  console.log(processedImage);
</script>

<div class="post-item">
  <a data-sveltekit-prefetch class="title" href="/posts/{slug}"
    ><h2>{title}</h2></a
  >
  <img width="800" height="300" src={processedImage} alt={title} />
  <Categories {categories} />
  <p>{description}</p>
</div>

<style>
  .post-item {
    margin-bottom: 3rem;
  }
  .title {
    text-decoration: none;
  }
  .title:hover {
    text-decoration: underline;
  }
  h2 {
    font-size: 1.8rem;
  }
  img {
    object-fit: cover;
    object-position: center;
  }
  @media screen and (max-width: 768px) {
    img {
      height: 200px;
      object-fit: contain;
      object-position: center;
    }
  }
</style>
