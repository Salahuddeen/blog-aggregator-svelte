<script>
    export let blog;
    const parser = new DOMParser();
    const htmlDoc = parser.parseFromString(blog.description, 'text/html')

    const openLink = () => (window.open(blog.link, "blank"));
    

</script>

<div class='card bg-semi-transparent border-primary mb-3' on:click="{openLink}">
    <div class="card-body">
        <h5 class="card-title">{blog.title}</h5>
        <p>{htmlDoc.body.textContent}</p>
        <div class="row timestamp">
            <p>Last Updated: {blog.UpdatedAt}</p>
        </div>
    </div>
</div>

<style>


.card{
    margin:10px;
    background-color:rgba(72, 161, 177, 0.10);
}

.card-title{
    color: rgba(18, 243, 74, 0.945);
    font-size: 2rem;
    text-align: left;
}

.timestamp{
    color:rgba(95, 218, 255, 0.25);
    text-align: right;
}

</style>