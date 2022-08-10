
<script>
	import PostCard from "../lib/PostCard.svelte";
	import SimilerPosts from "../lib/SimilerPosts.svelte";
	import Note from "../lib/Note.svelte";
	import Comments from "../lib/Comments.svelte";
	import WriteComment from "../lib/WriteComment.svelte";

	let post_id;
	
	
	
</script>
<svelte:head>
	<title>حراج</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="container grid grid-cols-4 lg:grid-cols-6 m-auto transition-all" dir='rtl'>
	<div class="col-span-4">
		<PostCard {post_id} />
		<Note/>

		<WriteComment/>

		<Comments {post_id}/>
	</div>
	<div class="transition-all col-span-4 md:col-span-3 lg:col-span-2">
		<SimilerPosts {post_id}/>
	</div>
</div>
