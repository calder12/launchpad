<script>
	export let segment;
</script>

<style>
	nav {
		border-bottom: 1px solid rgba(255,62,0,0.1);
		font-weight: 300;
		padding: 0 1rem;
		position: fixed;
		width: 100%;
		background-color: #fff;
		z-index: 999;
	}

	ul {
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		float: left;
	}

	.selected {
		position: relative;
		display: inline-block;
	}

	.selected::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		background-color: rgb(255,62,0);
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 0.75em;
		display: block;
	}
	a:hover {
		text-decoration: underline;
	}
	.logo {
		width: 30px;
		height: auto;
		vertical-align: middle;
		margin-right: 0.5rem;
	}
</style>

<nav>
	
	<ul>
		<li><a class:selected='{segment === undefined}' href='.'><img src="/saucer.svg" class="logo" alt="launchpad logo">launchpad</a></li>
	</ul>
</nav>
