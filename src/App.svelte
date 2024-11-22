<script>
    import Question from "./lib/Question.svelte";
    import questions from "./questions.json";

    const urlParams = new URLSearchParams(window.location.search);
    const teams = (urlParams.get('teams') - 0) || 5;

    let points = Array(teams).fill(0);

</script>



<main class="flex flex-col w-screen h-screen items-center p-5 text-white">
    <span class="text-5xl">RISKUJ!</span>
    <div class="grid grid-rows-6 grid-flow-col gap-3 grid-cols-5">
        {#each questions as question}
            <div class="flex items-center justify-center text-3xl p-2">{question.name}</div>
            {#each question.values as [text, anwser, used], index}
                <Question {text} {anwser} {index} bind:used={used} bind:points={points}></Question>
            {/each}
        {/each}
    </div>
    <table class="fixed bottom-1 right-1">
        {#each points as value, group}
            <tr><td>{group + 1}</td><td>{value}</td></tr>
        {/each}
    </table>
</main>

