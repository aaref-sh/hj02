
<script>
    import {fade,slide,scale} from 'svelte/transition';

    let tags = ["منزل","للايجار","مفروش"];
    let images = ['src/assets/1.jpg','src/assets/2.jpg','src/assets/3.jpg','src/assets/4.jpg','src/assets/5.jpg','src/assets/6.jpg'];
	
    export let publisher_id;
    export let post_id;
    let messeging = false;
    let img_name ;
    let previewing = false;
    let sending = 0;

	let post;
    post = {
		id: 1,
		publisher: "محمد عارف الشامي",
		publisher_id: "2",
		title: "شقة مفروشة للإيجار",
		body:"lurem",
		date: "4/1/2021 11:41",
		edited:"5/1/2021 13:41",
		views:"7",
		location:"سوريا - حماه",
		price: 4500
	};


    const PreviewImage = (e) => {
        img_name=e;
        previewing=!previewing;
    }
    const messagebox = ()=>{
        messeging=!messeging;
    }
    const send =() =>{
        sending = true;
    }
</script>


{#if previewing}
<div transition:fade={{duration:150}} on:click={PreviewImage}  class="fixed grid content-center z-10 top-0 left-0 right-0 bottom-0 bg-gray-800/80">
    <span class="fixed top-0 right-0 text-red-50 text-6xl select-none">×</span>   
    <img src="{img_name}" alt="" class="m-auto max-w-full" >
</div>
{/if}

{#if messeging}
<div transition:fade={{duration:150}} on:click|self={messagebox} class="fixed grid content-center z-10 top-0 left-0 right-0 bottom-0 bg-gray-800/80">
    <span on:click={messagebox} class="fixed top-0 right-0 text-red-50 text-6xl select-none">×</span>   
    <div class="messagebox overflow-hidden m-auto w-4/5 sm:w-96 h-min red-border bg-yellow-50/[98]  ">
        <h2 class="messegebox-header p-3 bg-gradient-to-r text-center 
        text-red-900 from-yellow-50 via-red-400/[.15] to-yellow-50">
            اكتب رسالة إلى publisher
        </h2>
        <hr class="spacer">
        {#if sending == false}
            
        <div class="messagebox-body my-5 mx-8 min flex flex-col">
            <textarea class="m-auto p-2 w-full rounded-md border-2 outline outline-0 hover:outline-1 active:outline-3 outline-red-600 border-red-700 focus:outline-none focus:ring focus:ring-red-300" rows="4" maxlength="150" />
            <button on:click={send} class="m-auto mt-4 block btn-std">إرسال</button>
        </div>
        {:else}
        <span class=" m-auto p-4 material-symbols-outlined text-green-600">
            check
        </span>
        {/if}
    </div>
</div>
{/if}

<div class="post-container transition-all m-2 overflow-hidden red-border">
    <div class="post-header transition-all m-auto py-4 px-8 text-gray-800 bg-gradient-to-r from-white/20 to-red-300/20">
        <h2 class="post-title transition-all text-red-900 text-2xl md:text-4xl ">
            {post.title}
        </h2>
        <div class="post-info gap-y-1 transition-all grid grid-cols-1 pr-2 sm:grid-cols-2 md:grid-cols-3 my-4">

            <a href="./users/{post.publisher_id}" class="post-header-item">
                <span class="material-symbols-outlined">
                    person
                </span> &nbsp;الناشر:&nbsp;
                {post.publisher}
            </a>
            <a href="./city/{post.location}" class="post-header-item">
                <span class="material-symbols-outlined">
                    location_on
                </span> &nbsp;العنوان:&nbsp;
                {post.location}
            </a>
            <div class="post-header-item">
                <span class="material-symbols-outlined">
                    visibility
                </span> &nbsp;المشاهدات:&nbsp;
                {post.views}
            </div>
            <div class="post-header-item">
                <span class="material-symbols-outlined">
                    payments
                </span> &nbsp;السعر:&nbsp;
                {post.price}
            </div>
            <div class="post-header-item">
                <span class="material-symbols-outlined">
                    schedule
                </span> &nbsp;تاريخ النشر:&nbsp;
                {post.date}
            </div>
            {#if post.edited != "null"}
            <div class="post-header-item">
                <span class="material-symbols-outlined">
                    edit_square
                </span> &nbsp;تاريخ التعديل:&nbsp;
                {post.edited}
            </div>
            {/if}
        </div>
    </div>
    
    <hr class="spacer"/>
    <div class="post-body text-lg text-gray-700/[.95] py-4 px-6">
        <slot name='post-body'>
            <span class="missing">Unknown body</span>
        </slot>
        <div class="images-grid grid grid-cols-2 justify-items-center sm:grid-cols-3 lg:gap-5 lg:grid-cols-4 gap-3 my-5">
            {#each images as image}
                <div on:click={()=>PreviewImage(image)} class="post-image sm:brightness-50 hover:brightness-100 duration-300 transition-all bg-cover border border-red-900/40 hover:shadow-xl hover:scale-110 rounded-md h-40 w-full shadow-md" 
                style="background-image: url('{image}');">

                </div>
            {/each}
        </div>
    </div>

    <div class="contact my-2 mx-6 flex justify-start items-center">
        التواصل: 
        <button class="transition-all flex items-center px-1 mx-1 text-red-900 hover:text-white rounded hover:bg-red-700 border border-red-700 ">
            <span class="material-symbols-outlined">
                smartphone
            </span>
            0951985386
        </button>
        
        <a href="mailto:m.aaref-sh@hotmail.com" class="transition-all flex items-center px-1 mx-1 text-red-900 hover:text-white rounded hover:bg-red-700 border border-red-700">
            <span class="material-symbols-outlined">
                mail
            </span>
            m.aaref-sh@hotmail.com
        </a>
    </div>

    <div class="tags flex justify-between items-center my-2 mx-6  border-r-4 border-r-red-700">
        <div class="px-1">{#each tags as tag}
            <a href="./tags/{tag}" class="post-tag px-1 text-white bg-red-700 rounded-xl">{tag}</a>
        {/each}</div>
            <button class="btn-std flex justify-center ">
                التالي
                <span class="material-symbols-outlined">
                    arrow_back
                </span>
            </button>
    </div>
</div>
<div class="flex red-border m-2">
    <button on:click={messagebox} class="post-buttons">
        <span class="material-symbols-outlined">
            mail
        </span>
        مراسلة
    </button>
    <button class="post-buttons separator">
        <span class="material-symbols-outlined">
            favorite
        </span>
        أعجبني
    </button>
    <button class="post-buttons separator">
        <span class="material-symbols-outlined">
            share
        </span>
        مشاركة
    </button>
    <button class="post-buttons separator">
        <span class="material-symbols-outlined">
            flag
        </span>
        إبلاغ
    </button>
</div>

<style>
    @import '../app.css';
    .post-buttons{
        @apply flex justify-center flex-auto transition-all bg-gradient-to-r hover:via-red-400/20 
        text-red-900 from-red-400/5 via-red-400/10 to-red-400/5;
    }
    .separator{
        @apply border-r border-red-700/[.9];
    }

</style>