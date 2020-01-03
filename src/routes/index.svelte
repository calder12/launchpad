<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`index.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  export let posts;
</script>

<style>
	h1 {
		text-align: center;
		margin: 0 auto;
	}

</style>

<svelte:head>
	<title>Launchpad</title>
</svelte:head>
<div>
<h1>Launchpad</h1>

  <ul>
    {#each posts as post}
      <li>
        <a rel="prefetch" href="/{post.slug}">{post.title}</a>
      </li>
    {/each}
  </ul>
</div>