<script>
    let url;
    let result = null;
    let formData = new FormData();

    async function doPost () {
        formData.append('url', url)
        const res = await fetch('http://localhost:8682/blog', {
            method: 'POST',
            body: formData,
            mode: "no-cors"
        })

        const status = await res.data()
        location.reload();
        formData = new FormData();
    }
</script>

<div class="row title">
    <div class="col title" >LinkWe Blog Aggregator</div>
    <div class="col">
        <input bind:value={url}  placeholder="Input a blog url here" />
        <button type="button" on:click={doPost}> Submit </button>
    </div>
</div>

<style>
.title{
    color: rgba(18, 243, 74, 0.945);
    font-size: 1.25rem;
    text-align: left;
    vertical-align: middle;
}
</style>