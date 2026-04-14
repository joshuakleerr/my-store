<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>Kleerr Market — demo storefront</title>
	<script
		async
		src="https://onionlike-jacklyn-scrawly.ngrok-free.dev/kleerr.core.staging.js?cid=991fb51b-b7e1-44ea-8091-384613621720&v=latest"
	></script>
</svelte:head>

<header class="site-header">
	<div class="inner">
		<a href="/" class="logo">Kleerr Market</a>
		<nav class="nav">
			<a href="/">Home</a>
			<a href="/shop">Shop &amp; videos</a>
			<a href="/checkout">Checkout</a>
		</nav>
		<div class="header-actions">
			<button type="button" class="ghost">Search</button>
			<button type="button" class="primary">Cart (0)</button>
		</div>
	</div>
</header>

<main>
	{@render children()}
</main>

<footer class="site-footer">
	<div class="inner footer-inner">
		<p class="muted">Dummy e-commerce demo — SvelteKit practice storefront.</p>
		<div class="btn-row">
			<button type="button">Help</button>
			<button type="button">Returns</button>
			<button type="button">Track order</button>
			<button type="button">Gift cards</button>
		</div>
	</div>
</footer>

<style>
	.site-header {
		position: sticky;
		top: 0;
		z-index: 10;
		background: rgba(255, 255, 255, 0.92);
		backdrop-filter: blur(10px);
		border-bottom: 1px solid var(--border);
	}

	.site-header .inner {
		max-width: 1120px;
		margin: 0 auto;
		padding: 0.85rem 1.25rem;
		display: flex;
		align-items: center;
		gap: 1.5rem;
		flex-wrap: wrap;
	}

	.logo {
		font-weight: 800;
		font-size: 1.15rem;
		color: var(--ink);
		letter-spacing: -0.02em;
	}

	.logo:hover {
		text-decoration: none;
		color: var(--accent);
	}

	.nav {
		display: flex;
		gap: 1.25rem;
		flex: 1;
	}

	.nav a {
		color: var(--ink);
		font-weight: 600;
	}

	.header-actions {
		display: flex;
		gap: 0.5rem;
	}

	main {
		min-height: calc(100vh - 180px);
	}

	.site-footer {
		border-top: 1px solid var(--border);
		background: var(--surface);
		margin-top: 2rem;
	}

	.footer-inner {
		padding: 1.5rem 1.25rem;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
	}
</style>
