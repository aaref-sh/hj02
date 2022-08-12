<script>
	import '../app.css';
	import Footer from '../lib/Footer.svelte';
	import Navbar from '../lib/Navbar.svelte';
</script>


<Navbar/>
<main>
	<slot />
</main>

<footer>
	<Footer />
</footer>
