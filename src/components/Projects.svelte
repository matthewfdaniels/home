<script>
    import ProjectData from "$data/projects.csv"
</script>

<div class="projects">
{#each ProjectData as project}
    <p><a href="{project["Link"]}" target=_blank>{project["Project"]}</a></p>
{/each}
</div>

<style>
    .projects {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(40vw, 1fr));
        gap: 10px;
    }
    p {
        font-weight: 700;
        font-size: 18px;
        margin: 0;
        margin-right: 10px;
        text-align: left;
    }

    a {
        text-decoration: underline;
        text-decoration-color: rgba(0,0,0,.3);
        border-bottom: none;
    }
</style>