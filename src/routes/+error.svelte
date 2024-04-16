<script>
    import { goto } from '$app/navigation';
    import { base } from '$app/paths';

    function backToHome() {
        goto(`${base}/`);
    }
</script>
<main>
    <h1 class=error>404</h1>
    <div class=text>
        <h1 class=caption>Are you lost <br/>among the flowers?</h1>
        <button class=back-button on:click={backToHome}>Let's get back to the right path!</button>
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        white-space: nowrap;
        background: radial-gradient(circle at 100% 100%, var(--background-primary) 0%, var(--background-secondary) 200%);
        /* background-color: var(--background-primary); */
        border-radius: 2em;
        /* box-shadow: 0 0 2em 2em var(--background-primary); */
        border: 0.5em solid var(--text-secondary);
        padding: 1em;
        transform: skewY(5deg);
    }
    .text {
        margin-left: 1.6em;
    }
    .error {
        font-size: 10em;
        line-height: 1em;
        color: var(--text-primary);
        margin: 0;
        text-shadow: 6px -3px var(--text-primary-background);
    }
    .caption {
        font-size: 2.4em;
        line-height: 1.2em;
        color: var(--text-primary);
        margin: 0;
    }
    .back-button {
        font-size: 1.4em;
        font-weight: bold;
        font-family: cursive, monospace;
        padding: 0.2em 1em 0.4em 1em;
        margin-top: 0.4em;
        background-color: var(--text-box-shadow);
        color: var(--text-secondary);
        border: none;
        border-radius: 0.5em;
        cursor: pointer;
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