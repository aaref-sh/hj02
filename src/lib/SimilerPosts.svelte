<script>
    export let post_id;
    let similers = [["1","1شخ","src/assets/1.jpg"],["2","2شخ","src/assets/2.jpg"],["3","3شخ","src/assets/3.jpg"],["4","4شخ","src/assets/4.jpg"]];

    /**
     * 
     * get similers from API
    */
</script>

<div class="transition-all similers-container m-2 overflow-hidden red-border">
    <div class="similers-header py-4 px-8 text-gray-800  bg-graded">
        <h2 class="similers-title text-center text-red-900 text-2xl lg:text-4xl ">
            عروض مشابهة
        </h2>
        
    </div>
    
    <hr class="spacer"/>
    <div class="similers-body grid grid-cols-2 gap-2 text-lg text-gray-700/[.95] py-4 px-6">
        {#if similers!=null}
            {#each similers as similer}
            <a href="./{similer[0]}">
                <div class="w-full h-40 bg-cover item-border shadow-md" style="background-image: url('{similer[2]}');">
                    <p class="bg-gradient-to-r from-red-400/10 via-red-400/40 to-red-400/10 text-center text-white"> {similer[1]}</p>
                </div>
            </a>
            {/each}
        {:else}
            <span class="missing">No similers posts</span>
        {/if}
        
    </div>
</div>
