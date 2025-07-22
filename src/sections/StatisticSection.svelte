<script>
    const message = `As of 2020, only <strong>35%</strong> of <strong>Black households</strong> in the Bay Area own their homes, compared to <strong>56% overall</strong>.`;
</script>

<div class="page">
    <h1>{@html message}</h1>
</div>

<style>
    :global(body, html) {
        margin: 0;
        padding: 0;
        height: 100%;
        width: 100%;
        background: #fffeed;
        /* REMOVE overflow: hidden; */
    }

    .page {
        /* Remove fixed height so it grows with content */
        width: 100vw;
        background-color: #fffeed;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 12rem;
        box-sizing: border-box;
        text-align: center;
        /* You can optionally add min-height if you want at least full viewport */
        min-height: 105vh;
        /* Allow flex to wrap content vertically */
        flex-direction: column;
    }

    h1 {
        font-family: "Merriweather", serif;
        color: rgb(3, 73, 109);
        font-weight: 300;
        font-size: clamp(1.5rem, 7.5vw, 6rem);
        line-height: 1.1;
        margin: 0;
        max-width: 60ch;
        word-wrap: break-word;
    }

    :global(h1 strong) {
        font-weight: 700;
    }
</style>
