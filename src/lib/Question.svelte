<script>
    export let text;
    export let anwser
    export let index;
    export let used;

    function click() 
    {
        if (used) {
            return;
        }
        used = true;
        // popup srandy jdu spat
    }
</script>

<div class="flex items-center justify-center text-4xl shadow-xl p-5 {used ? 'bg-stone-300 text-stone-400' : 'text-[#973350] bg-white'}" on:click={click}>
    {(index + 1) * 100}
</div>
