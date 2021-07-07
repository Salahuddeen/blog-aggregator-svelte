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
        <div class="bg-semi-transparent notFoundMessage notFoundMessage">
            <p>Put in a URL and Hit submit to aggregate some blogs</p>
            <iframe src="https://giphy.com/embed/uHD9t4kUUuTXTLMuuu" width="384" height="480" frameBorder="0" class="giphy-embed" allowFullScreen title="cat"></iframe><p><a href="https://giphy.com/gifs/traslacamara-funny-cat-animal-uHD9t4kUUuTXTLMuuu">via GIPHY</a></p>
            <p>Blogger cat says try https://www.thatcatblog.com/</p>
        </div>
    {/if}
{:else}
<p> loading.....blogs....</p> 
{/if}

<hr />
<style>
    .notFoundMessage {
        margin:50px;
        min-height: 240px;
        vertical-align: middle;
        font-size: x-large;
        padding:50px;
    }

</style>