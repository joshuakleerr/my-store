<script lang="ts">
	const products = [
		{
			name: 'Linen weekender',
			price: '$128',
			video:
				'https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4'
		},
		{
			name: 'Ceramic pour-over set',
			price: '$64',
			video: 'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerBlazes.mp4'
		},
		{
			name: 'Trail runner — dusk',
			price: '$189',
			video: 'https://storage.googleapis.com/gtv-videos-bucket/sample/ForBiggerJoyrides.mp4'
		}
	];

	let filterQuery = $state('');
	let category = $state('all');
	let maxPrice = $state('200');
	let reviewText = $state('');
</script>

<svelte:head>
	<title>Shop &amp; product videos — Kleerr Market</title>
</svelte:head>

<div class="page-wrap">
	<h1>Shop — watch product clips</h1>
	<p class="muted intro">
		Dummy listings with embedded sample videos. Use the filters (client-side only) and the review box
		below.
	</p>

	<section class="card filters">
		<h2>Filter &amp; search</h2>
		<form
			class="filter-form"
			onsubmit={(e) => {
				e.preventDefault();
			}}
		>
			<div class="field">
				<label for="q">Search</label>
				<div class="input-in-div">
					<input
						id="q"
						type="search"
						placeholder="Search products…"
						bind:value={filterQuery}
					/>
				</div>
			</div>
			<div class="row">
				<div class="field half">
					<label for="cat">Category</label>
					<select id="cat" bind:value={category}>
						<option value="all">All</option>
						<option value="apparel">Apparel</option>
						<option value="home">Home</option>
						<option value="footwear">Footwear</option>
					</select>
				</div>
				<div class="field half">
					<label for="price">Max price</label>
					<select id="price" bind:value={maxPrice}>
						<option value="100">Under $100</option>
						<option value="200">Under $200</option>
						<option value="500">Under $500</option>
					</select>
				</div>
			</div>
			<div class="btn-row">
				<button type="submit" class="primary">Apply filters</button>
				<button type="button">Clear</button>
				<button type="button">Save search</button>
				<button type="button">Share list</button>
			</div>
		</form>
	</section>

	<div class="toolbar btn-row">
		<button type="button">Grid</button>
		<button type="button">List</button>
		<button type="button">Sort: featured</button>
		<button type="button">Sort: price ↑</button>
		<button type="button">Sort: price ↓</button>
		<button type="button">Only in stock</button>
		<button type="button">Compare mode</button>
	</div>

	<ul class="product-grid">
		{#each products as p}
			<li class="card product">
				<video class="product-video" controls playsinline preload="metadata">
					<source src={p.video} type="video/mp4" />
					Your browser does not support the video tag.
				</video>
				<h3>{p.name}</h3>
				<p class="price">{p.price}</p>
				<div class="btn-row wrap">
					<button type="button" class="primary">Add to cart</button>
					<button type="button">Quick buy</button>
					<button type="button">Save</button>
					<button type="button">Details</button>
					<button type="button">Size chart</button>
				</div>
			</li>
		{/each}
	</ul>

	<section class="card review-box">
		<h2>Tell us what you think</h2>
		<form
			onsubmit={(e) => {
				e.preventDefault();
			}}
		>
			<div class="field">
				<label for="review">Your review (input area inside a styled div)</label>
				<div class="textarea-wrap">
					<textarea
						id="review"
						rows="4"
						placeholder="How was sizing? Shipping? Packaging?"
						bind:value={reviewText}
					></textarea>
				</div>
			</div>
			<div class="btn-row">
				<button type="submit" class="primary">Post review</button>
				<button type="button">Upload photos</button>
				<button type="button">Draft</button>
				<button type="button">Preview</button>
			</div>
		</form>
	</section>
</div>

<style>
	h1 {
		margin: 0 0 0.35rem;
		font-size: clamp(1.5rem, 3vw, 2rem);
	}

	.intro {
		margin: 0 0 1.25rem;
		max-width: 60ch;
	}

	.filters h2,
	.review-box h2 {
		margin: 0 0 0.75rem;
		font-size: 1.1rem;
	}

	.filter-form {
		max-width: 640px;
	}

	.input-in-div {
		padding: 0.5rem;
		border-radius: 10px;
		background: var(--bg);
		border: 1px solid var(--border);
	}

	.row {
		display: flex;
		gap: 1rem;
		flex-wrap: wrap;
	}

	.half {
		flex: 1;
		min-width: 140px;
	}

	.toolbar {
		margin: 1rem 0;
	}

	.product-grid {
		list-style: none;
		padding: 0;
		margin: 0;
		display: grid;
		gap: 1.25rem;
	}

	@media (min-width: 700px) {
		.product-grid {
			grid-template-columns: repeat(3, 1fr);
		}
	}

	.product h3 {
		margin: 0.75rem 0 0.15rem;
		font-size: 1.05rem;
	}

	.price {
		font-weight: 700;
		margin: 0 0 0.75rem;
		color: var(--accent);
	}

	.wrap {
		flex-wrap: wrap;
	}

	.review-box {
		margin-top: 1.5rem;
	}

	.textarea-wrap {
		padding: 0.65rem;
		border-radius: 10px;
		background: var(--bg);
		border: 1px dashed var(--border);
	}

	.textarea-wrap textarea {
		border: none;
		background: transparent;
		resize: vertical;
		min-height: 100px;
	}

	.textarea-wrap textarea:focus {
		outline: none;
	}
</style>
