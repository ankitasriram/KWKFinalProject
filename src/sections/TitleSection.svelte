<script>
    const title = "LOCKED \n OUT";
    const subtitle =
        "Examining Barriers to Black \n Homeownership in the Bay Area and Beyond";
</script>

<div class="screen">
    <h1>
        {#each title.split("\n") as line}
            <div>{line}</div>
        {/each}
    </h1>
    <h2>
        {#each subtitle.split("\n") as line}
            <div>{line}</div>
        {/each}
    </h2>
</div>

<style>
    :global(body, html) {
        margin: 0;
        padding: 0;
        height: 100%;
        background: black;
    }

    .screen {
        height: 100vh;
        width: 100vw;
        background-color: black;
        position: relative;
    }

    h1 {
        font-family: "DM Serif Text", serif;
        font-style: italic;
        position: absolute;
        top: 10rem;
        left: 15rem;
        font-size: clamp(5rem, 13vw, 17rem);
        line-height: clamp(4.5rem, 11vw, 15rem);
        color: #fffeed;
        margin: 0;

        text-shadow: 4px 4px 6px rgba(108, 138, 153, 0.8);
    }

    h1 div {
        line-height: inherit;
    }

    h2 {
        font-family: "Merriweather", serif;
        font-style: italic;
        position: absolute;
        bottom: 7rem;
        right: 10rem;
        font-size: clamp(1.2rem, 2.5vw, 2rem);
        line-height: clamp(1.2rem, 2.5vw, 2rem);
        color: #fff397;
        margin: 0;
        text-align: left; /* change this from right to left */
    }

    h2 div {
        line-height: inherit;
    }

    /* ---------- Responsive adjustments ---------- */
    @media (max-width: 1024px) {
        h1 {
            top: 6rem;
            left: 5rem;
        }

        h2 {
            bottom: 5rem;
            right: 6rem;
        }
    }

    @media (max-width: 600px) {
        h1 {
            top: 4rem;
            left: 2rem;
        }

        h2 {
            bottom: 3rem;
            right: 2rem;
            text-align: left;
        }
    }
</style>
