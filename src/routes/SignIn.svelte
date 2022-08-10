
<div class="post-container m-auto w-5/6 lg:w-4/5 overflow-hidden red-border">
    <div class="post-header py-4 px-8 bg-graded">
        <h2 class="post-title text-center text-red-900 text-2xl lg:text-4xl ">
            Sign In
        </h2>
        
    </div>
    
    <hr class="sapcer w-5/6 m-auto border-red-800 border-t "/>
    <div class="post-body text-lg text-gray-700/[.95] py-4 px-6 flex flex-col">
        <input placeholder="Username" type="text" class="w-full md:w-3/4 m-auto px-3 hover:bg-red-600/[.05] rounded-md outline outline-1 outline-red-600/50"/>

        <slot name='post-body'>
            <span class="missing">Unknown body</span>
        </slot>
    </div>
</div>
