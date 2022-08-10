<script>
    export let post_id;

    class comment {
        constructor(id, author, authorid, comment, date) {
            this.id = id;
            this.author = author;
            this.authorid = authorid;
            this.comment = comment;
            this.date = date;
        }
    }
    let cmt = new comment(1,"عارف",null,"شكرا اخي لكن السعر غالي بعض الشيء رغم أن البضاعة نفسها معروضة ارخص","1/2/2021 21:32");
    let comments = [];
    comments.push(cmt);
    comments.push(cmt);
    comments.push(cmt);
    comments.push(cmt);
    comments.push(cmt);
    /**
     * retrive comments from server
     * 
    */
</script>


<div class="comments mx-2">
    {#each comments as comment}
        <div class="comment bg-sky-50/30 border-2 border-gray-200
        text-gray-700 rounded-xl my-4 border-r-[3px] border-r-blue-900/70">
            <div class="comment-header border-b border-b-blue-900/70 p-2">
                <a class="text-blue-900" href="./users/{comment.authorid}">{comment.author}</a>  - 
                <span class="comment-date text-sm text-gray-400">
                    {comment.date}
                </span>
            </div>
            <div class="comment-body py-3 px-4 text-gray-600">
                {comment.comment}
            </div>
        </div>
    {/each}
</div>

<style>

</style>