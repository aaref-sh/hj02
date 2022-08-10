

<script>

    export let tags;

    let posts = [
        {
            id: "1",
            title:"شقة مفروشة للايجار",
            date:"1/5/2024 13:14",
            location:"سوريا - حماه",
            publisher:"محمد عارف الشامي",
            views:4,
            publisher_id:"2"
        },
        {
            id: "1",
            title:"شقة مفروشة للايجار",
            date:"1/5/2024 13:14",
            location:"سوريا - حماه",
            publisher:"محمد عارف الشامي",
            views:4,
            publisher_id:"2"
        }
    ];

</script>

<div class="posts">
    {#each posts as post}
        <div class="list-item">
            
            <a href="./posts/{post.id}" class="list-item-header text-lg text-red-900 ">
                
            </a>
        </div>
    {/each}
</div>

<style>


</style>