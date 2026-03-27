<script lang="ts">
	let shopperNote = $state('');
	let emailSignup = $state('');
</script>

<svelte:head>
	<title>Home — Kleerr Market</title>
</svelte:head>

<div class="page-wrap">
	<section class="hero card">
		<p class="eyebrow muted">Spring collection · dummy copy</p>
		<h1>Everyday goods, styled for real life</h1>
		<p class="lead">
			Browse featured categories, flash deals, and member perks. This page is a static demo with
			buttons, a quick signup form, and a place to type whatever you want.
		</p>
		<div class="btn-row hero-btns">
			<a href="/shop" class="btn primary">Shop featured</a>
			<button type="button">View lookbook</button>
			<button type="button">Up to 40% off</button>
			<button type="button">New arrivals</button>
			<button type="button">Editor&apos;s picks</button>
			<button type="button">Gift ideas</button>
		</div>
	</section>

	<section class="grid-two">
		<div class="card">
			<h2>Quick actions</h2>
			<p class="muted">Lots of buttons — pick your adventure.</p>
			<div class="btn-row dense">
				<button type="button">Women</button>
				<button type="button">Men</button>
				<button type="button">Home</button>
				<button type="button">Beauty</button>
				<button type="button">Tech</button>
				<button type="button">Sale</button>
				<button type="button">Stores near you</button>
				<button type="button">Size guide</button>
				<button type="button">Wishlist</button>
				<button type="button">Compare</button>
				<button type="button">Restock alerts</button>
				<button type="button">Live chat</button>
			</div>
		</div>

		<div class="card">
			<h2>Your note (text input in a div)</h2>
			<p class="muted">Type anything — it stays on this page only.</p>
			<div class="input-shell">
				<label for="shopper-note">Message to future you</label>
				<input
					id="shopper-note"
					type="text"
					placeholder="e.g. Order olive hoodie in M next Friday"
					bind:value={shopperNote}
				/>
			</div>
			{#if shopperNote}
				<p class="echo"><strong>You typed:</strong> {shopperNote}</p>
			{/if}
		</div>
	</section>

	<section class="card form-section">
		<h2>Stay in the loop</h2>
		<form
			class="newsletter"
			onsubmit={(e) => {
				e.preventDefault();
			}}
		>
			<div class="field">
				<label for="email">Email</label>
				<input id="email" type="email" placeholder="you@example.com" bind:value={emailSignup} />
			</div>
			<div class="btn-row">
				<button type="submit" class="primary">Subscribe</button>
				<button type="button">Maybe later</button>
				<button type="button">Text me instead</button>
			</div>
		</form>
	</section>
</div>

<style>
	.hero h1 {
		font-size: clamp(1.75rem, 4vw, 2.35rem);
		margin: 0.35rem 0 0.75rem;
		letter-spacing: -0.03em;
		line-height: 1.15;
	}

	.eyebrow {
		text-transform: uppercase;
		letter-spacing: 0.08em;
		font-size: 0.72rem;
		margin: 0;
	}

	.lead {
		max-width: 52ch;
		color: var(--muted);
		margin: 0 0 1.25rem;
	}

	.hero-btns {
		margin-top: 0.5rem;
	}

	.grid-two {
		display: grid;
		gap: 1.25rem;
		margin-top: 1.25rem;
	}

	@media (min-width: 768px) {
		.grid-two {
			grid-template-columns: 1fr 1fr;
		}
	}

	.dense {
		margin-top: 1rem;
	}

	.input-shell {
		margin-top: 0.75rem;
		padding: 1rem;
		border-radius: 10px;
		background: var(--bg);
		border: 1px dashed var(--border);
	}

	.echo {
		margin-top: 1rem;
		padding: 0.75rem 1rem;
		background: var(--bg);
		border-radius: 8px;
		font-size: 0.95rem;
	}

	.form-section {
		margin-top: 1.25rem;
	}

	.newsletter {
		margin-top: 0.75rem;
		max-width: 420px;
	}

	h2 {
		margin: 0 0 0.35rem;
		font-size: 1.2rem;
	}
</style>
