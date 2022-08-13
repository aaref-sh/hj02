
<script>
    import {fade} from 'svelte/transition';
    import Reset from '../lib/Reset.svelte';
    import SignUp from '../lib/SignUp.svelte';

    let resetting = false;
    let signing = false;
    const reset = () => {
        resetting = !resetting;
    };

    const signup = () => {
        signing= !signing;
    };
</script>

{#if resetting}
<div in:fade>
    <Reset on:click={reset}/></div>
{:else if signing}
<div in:fade>
    <SignUp on:click={signup}/></div>
{:else}

<div in:fade class="post-container m-auto w-5/6 md:w-[500px] std-border">
    <div class="post-header py-4 px-8 bg-graded">
        <h2 class="post-title text-center ">
            تسجيل الدخول
        </h2>
        
    </div>
    
    <hr class="sapcer w-5/6 m-auto"/>
    <div class="post-body text-lg text-gray-700/[.95] py-4 px-6 flex flex-col">
        <input placeholder="رقم الهاتف" type="number" 
        class=" std-textbox w-4/5  mb-4 m-auto"/>
        <input placeholder="كلمة المرور" type="password" 
        class=" std-textbox w-4/5 mb-4 m-auto"/>

        <div class="links mr-8 text-gray-400 text-sm">
            هل نسيت كلمة المرور؟ <button on:click="{reset}">إعادة تعيين كلمة المرور</button>
            <br>
            إذا لم يكن لديك حساب <button on:click="{signup}" >إنشئ حساب</button>
        </div>
        <button class="btn-std m-auto mt-3">دخول</button>
    </div>
</div>

{/if}

