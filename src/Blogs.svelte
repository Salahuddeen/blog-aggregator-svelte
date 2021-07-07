<script>
    let blog_data;

    import { onMount } from "svelte";
    import Blog from "./Blog.svelte";


    onMount(async () => {
        await fetch(`http://localhost:8682/posts`)
        .then(r => r.json())
        .then(data => {
            blog_data = data;
        });
    })
    
</script>
{#if blog_data} 
    {#if blog_data.total !== 0}
        {#each blog_data.items as blog}
            {#if blog.title !== 'About' && blog.title !== 'Privacy'}
                <Blog {blog} />
            {/if}
        {/each}
    {:else}
        <p> Sorry there are no blogs, Please use the input to add one </p>
    {/if}
{:else}
<p> loading.....blogs....</p> 
{/if}

<hr />
<style>

</style>