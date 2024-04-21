<script lang="ts">
    import { goto } from '$app/navigation';
    import { base } from '$app/paths';
    import questions from '$lib/question.json';
    import results from '$lib/result.json';
    import meanings from '$lib/meaning.json';
    var index = 0;
    var answers = "";
    $: question = index < questions.length ? questions[index]["question"] : "";
    $: choices = index < questions.length ? questions[index]["choices"] : {};
    $: result = index >= questions.length ? results[answers as keyof typeof results] : "";
    $: resultDisplay = index >= questions.length ? result.replaceAll("_", " ") : "";
    $: meaning = index >= questions.length ? meanings[result as keyof typeof meanings] : "";

    function selectAnswer(event: any) {
        answers += event.target.id;
        index++;
    }

    function backToHome() {
        index = 0;
        answers = "";
        goto(`${base}/`);
    }
</script>
<main>
    {#if index < questions.length}
        <h1 class="question">{question}</h1>
        <div class="choices">
            {#each Object.entries(choices) as [choice, text]}
                <button class="choice" on:click={selectAnswer} id={choice}>{text}</button>
            {/each}
        </div>
    {:else}
        <h1 class="result">You are a "{resultDisplay}"!</h1>
        <img class="image" width=300 src="/image/{result}.svg" alt={result} />
        <p class="meaning">Meaning: {meaning}</p>
        <button class="back" on:click={backToHome}>&lt;&lt; Back to Home</button>
    {/if}
</main>
<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 600px;
        align-items: center;
        transform: skewY(5deg);
    }
    .question {
        text-align: center;
        margin: 0;
        font-size: 2em;
        font-weight: bold;
        color: var(--text-primary);
        padding: 10px 30px 15px 30px;
        background-color: var(--text-primary-background);
        box-shadow: var(--text-box-shadow) 8px -4px;
        border-radius: 20px;
    }
    .choices {
        display: flex;
        flex-direction: column;
        gap: 1em;
        margin-top: 12px;
        transform: translateX(8px);
    }
    .choice {
        font-size: 1.4em;
        padding: 0.4em 1em;
        background-color: var(--text-box-shadow);
        color: var(--text-secondary);
        border: none;
        border-radius: 0.5em;
        cursor: pointer;
    }
    .choice:hover {
        background-color: var(--text-primary);
    }
    .result {
        font-size: 2.4em;
        font-weight: bold;
        color: var(--text-primary);
        padding: 10px 30px 15px 30px;
        margin: 0;
        background-color: var(--text-primary-background);
        box-shadow: var(--text-box-shadow) 8px -4px;
        border-radius: 20px;
    }
    .image {
        margin: 20px;
        border-radius: 10px;
        background: radial-gradient(circle at 0% 0%, var(--text-box-shadow) 0%, var(--background-primary) 150%);
        transform: translate(8px, -4px);
    }
    .meaning {
        font-size: 1.4em;
        text-align: center;
        color: var(--text-primary);
        width: 100%;
        margin: 0;
        padding: 5px 0 10px 0;
        border-radius: 10px;
        background-color: var(--text-primary-background);
        box-shadow: var(--text-box-shadow) 4px -2px;
    }
    .back{
        font-size: 1.2em;
        font-family: cursive, monospace;
        padding: 0 10px 5px 10px;
        margin-top: 0.4em;
        margin-left: auto;
        background-color: var(--text-box-shadow);
        color: var(--text-secondary);
        border: none;
        border-radius: 0.5em;
        cursor: pointer;
        transform: translateX(4px);
    }
    @media (max-width: 800px) {
        main {
            transform: scale(0.8) skewY(5deg);
        }
    }
    @media (max-width: 600px) {
        main {
            transform: scale(0.6) skewY(5deg);
        }
    }
    @media (max-width: 450px) {
        main {
            transform: scale(0.4) skewY(5deg);
        }
    }
</style>
  