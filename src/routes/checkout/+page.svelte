<script lang="ts">
	let orderNotes = $state('');
	let fullName = $state('');
	let address = $state('');
	let city = $state('');
	let coupon = $state('');
</script>

<svelte:head>
	<title>Checkout — Kleerr Market</title>
</svelte:head>

<div class="page-wrap checkout">
	<h1>Checkout</h1>
	<p class="muted">Dummy two-column checkout with forms and extra buttons.</p>

	<div class="checkout-grid">
		<section class="card">
			<h2>Shipping</h2>
			<form
				class="ship-form"
				onsubmit={(e) => {
					e.preventDefault();
				}}
			>
				<div class="field">
					<label for="name">Full name</label>
					<input id="name" type="text" autocomplete="name" bind:value={fullName} />
				</div>
				<div class="field">
					<label for="addr">Address</label>
					<input id="addr" type="text" autocomplete="street-address" bind:value={address} />
				</div>
				<div class="row">
					<div class="field grow">
						<label for="city">City</label>
						<input id="city" type="text" bind:value={city} />
					</div>
					<div class="field zip">
						<label for="zip">ZIP</label>
						<input id="zip" type="text" inputmode="numeric" />
					</div>
				</div>
				<div class="btn-row">
					<button type="button">Use saved address</button>
					<button type="button">Ship to store</button>
					<button type="button">Address book</button>
				</div>
			</form>
		</section>

		<section class="card">
			<h2>Order notes</h2>
			<p class="muted small">Another text field, wrapped in a div for layout.</p>
			<div class="notes-shell">
				<label for="notes">Delivery instructions</label>
				<input
					id="notes"
					type="text"
					placeholder="Gate code, leave on porch, etc."
					bind:value={orderNotes}
				/>
			</div>
			{#if orderNotes}
				<p class="preview muted">Preview: {orderNotes}</p>
			{/if}

			<h2 class="spaced">Promo &amp; payment</h2>
			<form
				class="promo-form"
				onsubmit={(e) => {
					e.preventDefault();
				}}
			>
				<div class="field inline-field">
					<label for="coupon">Coupon code</label>
					<div class="coupon-row">
						<input id="coupon" type="text" placeholder="SAVE10" bind:value={coupon} />
						<button type="button" class="primary">Apply</button>
					</div>
				</div>
				<div class="btn-row pay-actions">
					<button type="button">Pay with card</button>
					<button type="button">PayPal</button>
					<button type="button">Apple Pay</button>
					<button type="button">Klarna</button>
					<button type="button">Gift card</button>
					<button type="button">Use rewards</button>
				</div>
				<div class="btn-row final">
					<button type="submit" class="primary wide">Place order (demo)</button>
					<button type="button">Save for later</button>
				</div>
			</form>
		</section>
	</div>

	<section class="card summary">
		<h2>Cart summary</h2>
		<ul class="lines">
			<li><span>Linen weekender</span><span>$128.00</span></li>
			<li><span>Shipping</span><span>$12.00</span></li>
			<li><span>Tax (est.)</span><span>$11.20</span></li>
			<li class="total"><span>Total</span><span>$151.20</span></li>
		</ul>
		<div class="btn-row">
			<button type="button">Edit cart</button>
			<button type="button">Add protection plan</button>
			<button type="button">Schedule delivery</button>
			<button type="button">Print receipt</button>
		</div>
	</section>
</div>

<style>
	h1 {
		margin: 0 0 0.35rem;
	}

	.checkout > .muted {
		margin-bottom: 1.25rem;
	}

	.checkout-grid {
		display: grid;
		gap: 1.25rem;
	}

	@media (min-width: 900px) {
		.checkout-grid {
			grid-template-columns: 1fr 1fr;
			align-items: start;
		}
	}

	h2 {
		margin: 0 0 0.75rem;
		font-size: 1.1rem;
	}

	.spaced {
		margin-top: 1.5rem;
	}

	.row {
		display: flex;
		gap: 1rem;
	}

	.grow {
		flex: 1;
	}

	.zip {
		width: 120px;
		flex-shrink: 0;
	}

	.notes-shell {
		padding: 1rem;
		border-radius: 10px;
		background: var(--bg);
		border: 1px solid var(--border);
	}

	.preview {
		margin-top: 0.75rem;
		font-size: 0.9rem;
	}

	.coupon-row {
		display: flex;
		gap: 0.5rem;
		align-items: stretch;
	}

	.coupon-row input {
		flex: 1;
	}

	.pay-actions {
		margin: 1rem 0;
	}

	.final {
		margin-top: 0.5rem;
	}

	.wide {
		padding-left: 1.5rem;
		padding-right: 1.5rem;
	}

	.summary {
		margin-top: 1.25rem;
	}

	.lines {
		list-style: none;
		padding: 0;
		margin: 0 0 1rem;
	}

	.lines li {
		display: flex;
		justify-content: space-between;
		padding: 0.4rem 0;
		border-bottom: 1px solid var(--border);
		font-size: 0.95rem;
	}

	.lines li.total {
		font-weight: 800;
		border-bottom: none;
		padding-top: 0.75rem;
	}

	.small {
		font-size: 0.85rem;
		margin: 0 0 0.5rem;
	}
</style>
