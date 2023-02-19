<script>

    let skills = [

        {
            id:1,
            name:'html'
        },
        {
            id:2,
            name:'css'
        },
        {
            id:3,
            name:'javascript'
        }
    ]
</script>

<div class="Skills">

    {#each skills as skill,i}

    <li>
       {skill.id}-. {skill.name}
    </li>
    {/each}
</div>