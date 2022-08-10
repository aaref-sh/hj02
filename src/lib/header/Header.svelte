<script>
	import { page } from '$app/stores';
</script>

<header>
	<nav>
		<ul class="flex gap-2">
			<li class:active={$page.url.pathname === '/'}><a sveltekit:prefetch href="/">Home</a></li>
		
			<li class:active={$page.url.pathname === '/SignIn'}><a sveltekit:prefetch href="/SignIn">SignIn</a></li>
		</ul>
	</nav>
</header>

