<script>
    import { blur } from "svelte/transition";
    import PopUp from "./PopUp.svelte";

    export let text;
    export let anwser
    export let index;
    export let used;
    export let points;

    const value = (index + 1) * 100;

    let state = false;

    function click() 
    {
        if (used) {
            return;
        }
        used = true;
        state = true;
    }
</script>

<PopUp bind:state={state} {text} {anwser} bind:points={points} {value}></PopUp>

<div class="flex items-center justify-center text-4xl p-5 {used ? 'bg-[#973350] text-[#973350] opacity-0' : 'text-[#973350] bg-white shadow-xl'}" on:click={click} transition:blur>
    {value}
</div>
