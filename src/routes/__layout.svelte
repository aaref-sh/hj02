<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
	import Footer from '../lib/Footer.svelte';
</script>

<Header />

<main>
	<slot />
</main>

<footer>
	<Footer />
</footer>
