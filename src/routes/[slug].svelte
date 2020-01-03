<script context="module">                                                                                                                                                                                                                                                                   
  export async function preload({ params, query }) {
    const res = await this.fetch(`_posts/${params.slug}.md`);

    if (res.status === 200) {
      return { postMd: await res.text() };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
	import { onMount } from 'svelte';
  import fm from 'front-matter';
  import marked from 'marked'
  import hljs from 'highlight.js';
  import  {fade}  from "svelte/transition";

  export let postMd;
  $: frontMatter = fm(postMd);
  $: post = {
    ...frontMatter.attributes,
    html: marked(frontMatter.body)
  };
console.log(postMd)
  onMount(async () => {
    document.querySelectorAll('pre code').forEach((block) => {
      hljs.highlightBlock(block);
    });
	});
</script>

<style>
	.content :global(h2) {
		font-size: 1.4em;
		font-weight: 500;
	}

	.content :global(ul) {
		line-height: 1.5;
	}

</style>

<svelte:head>
	<title>{post.title}</title>
</svelte:head>

<div class="container" transition:fade="{{duration: 200 }}">
<h1>{post.title}</h1>
<p>{post.date}</p>

<div class='content'>
	{@html post.html}
</div>
</div>
