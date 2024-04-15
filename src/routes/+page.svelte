<script lang="ts">
    import { goto } from '$app/navigation';
    import { base } from '$app/paths';

    function startQuiz() {
        goto(`${base}/quiz`);
    }
</script>

<main>
    <h2 class=verse-1>
        Roses are <span class=red>red</span>,
        <div class=ribbon-top></div>
        <div class=ribbon-bottom></div>
    </h2>
    <h2 class=verse-2>
        Violets are <span class=blue>blue</span>,
        <div class=ribbon-top></div>
        <div class=ribbon-bottom></div>
    </h2>
    <h3 class=pre-chorus>
        Let's find out,
        <div class=arrow></div>
    </h3>
    <h1 class=chorus>What flower are you?</h1>
    <button class=start-button on:click={startQuiz}>Begin Exploring &gt;&gt;</button>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        white-space: nowrap;
        transform: skewY(5deg) translateY(-14px);
    }
    h1, h2, h3 {
        margin: 0;
    }
    .red {
        color: var(--text-red);
    }
    .blue {
        color: var(--text-blue);
    }
    .verse-1 {
        font-size: 2.4em;
        color: var(--text-primary);
        transform: translate(-3.9em, 2.2rem);
        padding: 0 1.8rem 0 1.4rem;
        background-color: var(--text-primary-background);
    }
    .verse-1 .ribbon-bottom {
        width: 0;
        height: 0;
        border-left: 50px solid transparent;
        border-bottom: 50px solid var(--text-primary-background);
        position: absolute;
        bottom: 0;
        left: -30px;
    }
    .verse-1 .ribbon-top {
        width: 0;
        height: 0;
        border-left: 50px solid transparent;
        border-top: 50px solid var(--text-primary-background);
        position: absolute;
        top: 0;
        left: -30px;
    }
    .verse-2 {
        font-size: 2.4em;
        color: var(--text-primary);
        transform: translateX(4em);
        padding: 0 1rem;
        background-color: var(--text-primary-background);
    }
    .verse-2 .ribbon-bottom {
        width: 0;
        height: 0;
        border-right: 50px solid transparent;
        border-bottom: 50px solid var(--text-primary-background);
        position: absolute;
        bottom: 0;
        right: -30px;
    }
    .verse-2 .ribbon-top {
        width: 0;
        height: 0;
        border-right: 50px solid transparent;
        border-top: 50px solid var(--text-primary-background);
        position: absolute;
        top: 0;
        right: -30px;
    }
    .pre-chorus {
        font-size: 1.8em;
        color: var(--text-secondary);
        padding: 0 10px;
        transform: translate(-8.6em, 0.4rem);
        background-color: var(--text-secondary-background);
        box-shadow: var(--text-box-shadow) 7px -7px;
        border-radius: 10px;
    }
    .pre-chorus .arrow {
        width: 0;
        height: 0;
        border-left: 20px solid transparent;
        border-top: 10px solid var(--text-secondary-background);
        position: absolute;
        bottom: -9px;
        left: 80%;
    }
    .chorus {
        font-size: 4em;
        font-weight: bold;
        color: var(--text-primary);
        padding: 0 20px 5px 20px;
        background-color: var(--text-primary-background);
        box-shadow: var(--text-box-shadow) 6px -6px;
        border-radius: 20px;
    }
    .start-button {
        font-family: cursive, monospace;
        font-size: 1.6em;
        font-weight: bold;
        padding: 0px 20px 5px 20px;
        background-color: var(--text-box-shadow);
        color: var(--text-secondary);
        border: none;
        border-radius: 10px;
        box-shadow: 
            var(--text-primary-background) 6px -6px,
            var(--text-box-shadow) 12px -12px;
        transform: translateX(6em);
        z-index: -1;
        cursor: pointer;
    }
    @media (max-width: 800px) {
        main {
            transform: scale(0.8) skewY(5deg) translateY(-14px);
        }
    }
    @media (max-width: 600px) {
        main {
            transform: scale(0.6) skewY(5deg) translateY(-14px);
        }
    }
    @media (max-width: 450px) {
        main {
            transform: scale(0.4) skewY(5deg) translateY(-14px);
        }
    }
</style>