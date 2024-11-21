<script>
    import Question from "./lib/Question.svelte";
    import questions from "./questions.json";

</script>

<main class="flex flex-col w-screen h-screen items-center p-5 text-white">
<span class="text-5xl">RISKUJ!</span>
<div class="grid grid-rows-6 grid-flow-col gap-3 grid-cols-2">
    {#each questions as question}
        <div class="flex items-center justify-center text-3xl p-2">{question.name}</div>
        {#each question.values as [text, anwser, used], index}
            <Question {text} {anwser} {index} {used}></Question>
        {/each}
    {/each}
    </div>
</main>

