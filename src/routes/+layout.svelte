<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<title>Labs: Rindra Aniko</title>
	<meta name="description" content="eksperimen yang dilakukan rindra aniko file-file sementara semua termuat disini" />
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}
