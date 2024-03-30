<script>
    import ProjectData from "$data/projects.csv"

    ProjectData.forEach(d=> {
        d.RoleSplit = JSON.stringify(d.Role).replace(/['"]+/g, '').split(",");
    })

    $: console.log(ProjectData)
</script>


<p class="subhead" style="margin-bottom:10px;">Authored</p>
<div class="projects">
    {#each ProjectData.filter(d => d.Role == "Author") as project}
        <p><a href="{project["Link"]}" target=_blank>{project["Project"]}</a>
            {#if project.Entity !== "The Pudding"}
                <span class="with-entity">with {project.Entity}</span>
            {/if}
        </p>
    {/each}
</div>

<p class="subhead" style="margin-bottom:10px;">Misc</p>
<div class="projects projects-misc">
    {#each ProjectData.filter(d => d.Role !== "Author") as project}
        <p><a href="{project["Link"]}" target=_blank>{project["Project"]}</a>
            {#if project.Entity !== "The Pudding"}
                <span class="with-entity">with {project.Entity}</span>
            {/if}
            {#each project.RoleSplit as role}
                <span class="tag {role}">{role}</span>
            {/each}
        </p>
    {/each}
</div>

<style>
    .with-entity {
        font-size: 12px;
        font-weight: 800;
        text-transform: uppercase;
    }
    .tag.Designer {
        /* background-color: #d0ffff; */
    }
    .projects {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
        gap: 10px;
        margin-bottom: 50px;
    }
    .projects-misc {
        grid-template-columns: 1fr;
    }
    .tag {
        font-size: 11px;
        background-color: #eee;
        padding: 2px 10px;
        border-radius: 5px;
        text-transform: uppercase;
        font-weight: 800;
        margin-right: 10px;
    }
    @media only screen and (max-width: 410px) {
        .projects {
            grid-template-columns: 1fr;
        } 
    }
</style>