<script>
    export let data;
</script>

<div class="awards">
    {#each data as award}
        <p>{award.text}, <a href="{award.link}">{award.project}</a></p>
    {/each}
</div>


<style>
.awards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
    gap: 10px;
    margin-bottom: 50px;
}
p {
    font-weight: 800;
}
a {
    opacity: .6;
}

@media only screen and (max-width: 410px) {
    .awards {
        grid-template-columns: 1fr;
    }
    
}

</style>