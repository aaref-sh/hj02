<script>
    import{page}from"$app/stores";

    let tabs = [
        {
            // DO NOT remove this 
            path:"start",
        },
        {
            path:"/",
            text:"الرئيسية",
            icon:"Home",
        },
        {
            path:"/post",
            text:"منشور",
            icon:"sell",
        },
        {
            path:"/info",
            text:"تعليمات",
            icon:"info",
        },
        {
            // DO NOT remove this 
            path:"end",
        },

    ];

    let pag = $page.url.pathname;

    function is_next (page , tab){
        let index = tabs.findIndex(x => x.path == page);
        if(index < tabs.length-1)
            return tabs[index+1] == tab;
        return false;
    };
    function is_befor (page , tab){
        let index = tabs.findIndex(x => x.path == page);
        if(index > 0)
            return tabs[index-1] == tab;
        return false;
    };
    function is_active (page , tab){
        return tabs.find(x => x.path == page) == tab;
    };
    const classes = (page,tab)=>{
        if(is_active(page,tab)) return "nav-item-active";
        if(is_next(page,tab)) return "next-to-active";
        if(is_befor(page,tab)) return "befor-active";
        return "";
    };
    
</script>


<nav class="w-full h-8 pt-2  bg-sky-600 text-white mb-12">

    <div class=" flex w-full h-12 ">
        <div class="navbar flex flex-none h-12 items-center text-2xl" >
            <div class=" nav-item {classes($page.url.pathname,tabs[0])}" />
            {#each tabs as tab}
                {#if tab.path != "end" &&  tab.path != "start"}
                    <a href="{tab.path}" class=" nav-item {classes($page.url.pathname,tab)}" >
                        <span class="material-symbols-outlined">
                            {tab.icon}
                        </span> &nbsp;
                        {tab.text}
                    </a>
                {/if}
            {/each}
            <div class=" nav-item {classes($page.url.pathname,tabs[tabs.length-1])}" />
        </div>
        
        <div class="flex-auto  bg-sky-600 pl-8 flex justify-end">
        
        
            <div class="login flex -mt-2 items-center hover:text-white transition-all text-lg text-blue-100 pl-6">
                <span class="material-symbols-outlined">
                    login
                </span> 
                الدخول
            </div>
            <div class="logo w-16 h-16 -mt-2 text-4xl flex items-center">
                logo
            </div>
        </div>
    </div>
</nav>
<!-- <div class="-mt-5 w-full bg-white h-16"></div> -->

<style>
    .next-to-active{
        @apply rounded-br-3xl;
    }
    .befor-active{
        @apply rounded-bl-3xl;
    }
    .nav-item{
        @apply transition-all flex items-center h-full bg-sky-600 text-white px-5;
    }
    .nav-item-active{
        @apply transition-all bg-transparent bg-white rounded-t-3xl text-sky-600;
    }

</style>