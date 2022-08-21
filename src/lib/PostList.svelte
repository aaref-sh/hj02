

<script>

let postss = [];
    var requestOptions = {
    method: 'GET',
    redirect: 'follow'
    };

    fetch("https://localhost:5000/api/Users/PostsGetAll", requestOptions)
    .then(response => response.text())
    .then(result =>{
        postss = [];
        postss = JSON.parse(result);
    } )
    .catch(error => console.log('error', error));



    export let tags;

    let posts = [
        {
            id: "1",
            title:"شقة مفروشة للايجار",
            date:"1/5/2024 13:14",
            location:"سوريا - حماه",
            publisher:"محمد عارف الشامي",
            views:4,
            image:"src/assets/1.jpg",
            publisher_id:"2"
        },
        {
            id: "1",
            title:"شقة مفروشة للايجار",
            date:"1/5/2024 13:14",
            location:"سوريا - حماه",
            publisher:"محمد عارف الشامي",
            views:4,
            image:"src/assets/1.jpg",
            publisher_id:"2"
        }
    ];
</script>

<div class="list-container m-1 sm:m-2">
    {#if postss.length == 0}
        لا يوجد نتائج تطابق البحث
    {/if}
    {#each postss as post}
        <div class="p-1 mt-2 border border-blue-200/70 rounded shadow-sm hover:shadow hover:bg-cyan-50/30 transition-all flex">
            <a href="./{post.id}" class="h-ful w-full flex-auto">
                <h3 class="list-title px-5 py-2 text-blue-1000 text-lg md:text-2xl">
                    {post.title}
                </h3>
                <hr class="border-t border-sky-300/50 ml-1">
                <div class="grid grid-cols-1 sm:grid-cols-2 pt-2  px-3">
                    <a href="./users/{post.userId}" class="post-header-item">
                        <span class="material-symbols-outlined">
                            person
                        </span> &nbsp;
                        {post.userName}
                    </a>
                    <div class="post-header-item">
                        <span class="material-symbols-outlined">
                            schedule
                        </span> &nbsp;
                        {post.created}
                    </div>
                    <div class="post-header-item">
                        <span class="material-symbols-outlined">
                            visibility
                        </span> &nbsp;
                        {post.views}
                    </div>
                    <div class="post-header-item">
                        <span class="material-symbols-outlined">
                            thumb_up
                        </span> &nbsp;
                        {post.likes}
                    </div>
                </div>
            </a>
            {#if post.picture!=""}
                <div class="post-image flex-none h-24 w-24 std-border bg-cover rounded-md" 
                    style="background-image: url({post.picture});">
                </div>
            {/if}
        </div>
    {/each}
</div>


<style>


</style>