<script>   
    import { onMount } from "svelte";
    import { blur } from "svelte/transition";
    export let state;
    export let text;
    export let anwser;
    export let points;
    export let value;
    let display_anwser = false; // WHAT THE FUCK IS THIS WHY ITS NOT SOLID AUTOMATON

    function close(event) {
        if (!state) {
            return;
        }

        if (display_anwser && event.key.search(/^[1-9]$/) == 0) {
            let group = event.key - 1;
            if (points[group] == undefined) {
                return;
            }

            console.log(value);

            points[group] += value
            console.log(points);
            state = false;
            display_anwser = false;
            return;
        }

        if (event.key == " ") {
            display_anwser = true;
            return;
        }
    }

    onMount(() => {
        window.addEventListener("keydown", close);

        return () => {
            window.removeEventListener("keydown", close);
        }
    })
</script>

{#if state}
    <div class="fixed top-0 left-0 w-screen h-screen bg-black/50 flex items-center justify-center" transition:blur={{ amount: 1 }} >
        <div class="bg-white text-[#973350] w-3/4 h-3/4 text-4xl flex flex-col items-center justify-center p-5">
            {#if display_anwser}
                <div class="text-2xl">Správná odpověď</div>
                <div>{@html anwser}</div>
            {:else}
                {text}
            {/if}
        </div>
    </div>
{/if}
