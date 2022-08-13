

<script>
    import PostList from "../lib/PostList.svelte";
</script>
<div class="container m-auto">
    <div class="index-main w-full xl:w-5/6 m-auto grid grid-cols-3 md:grid-cols-4">
        <div class="index-sidebar m-2 col-span-2 sm:col-span-1  ">
            <select name="" id="" class="w-full transition-all px-2 py-1 border border-sky-600 rounded-lg focus:outline-none focus:ring focus:ring-sky-300">
                <option value="All">الكل</option>
                <option value="car">سيارات</option>
            </select>
        </div>
        <div class="col-span-4 sm:col-span-3 transition-all">
            <PostList />
        </div>
    </div>
</div>