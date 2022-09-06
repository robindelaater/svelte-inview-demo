<script>
	import { inview } from 'svelte-inview'
	import { fade } from 'svelte/transition'

	export let classes

	let isInView = false
	const options = {
		rootMargin: '-20%',
		unobserveOnEnter: false
	}
</script>

<div
	use:inview={options}
	on:change={(event) => {
		const { inView } = event.detail
		isInView = inView
	}}
	class="container mx-auto {classes}"
>
	{#if isInView}
		<p>In view</p>
		<div transition:fade={{ duration: '200' }}>
			<slot />
		</div>
	{:else}
		<p>Out of view</p>
	{/if}
</div>
