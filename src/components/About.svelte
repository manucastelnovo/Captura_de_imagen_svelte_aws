<script>
    let someText = `Front end developer`
    let count = 0;
    let style = { darkMode: false}

    function handleClick(){
        count +=1;
    }

    function toggle(){
        style.darkMode = !style.darkMode;
        window.document.body.classList.toggle("dark-mode")
    }

</script>

<style>
p{
    color: var(--theme-color);
}

</style>

<div class="About">
<p> 
    {someText}
    <button on:click={handleClick}>
        Click
        {count === 0 ? '' : count}
    </button>

    <button on:click={toggle}>
		DarkMode
	</button>
</p>

    { #if style.darkMode}
        <p>estoy en dark mode</p>
    { :else }
        <p>estoy en modo normal </p>
    {/if}
    
</div>
