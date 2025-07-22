<script>
    let { layout, sticky, scrolly, backgroundColor = "#063244" } = $props();
</script>

<div class="wrapper {layout}" style="background-color: {backgroundColor};">
    <div class="sticky">
        {@render sticky()}
    </div>

    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
    .wrapper {
        background-color: #f7f5eb;
        padding-top: 1rem;
        padding-bottom: 2rem;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
    }

    .left .scrolly {
        order: 0;
    }
    .left .sticky {
        order: 1;
    }

    .right .scrolly {
        order: 1;
    }
    .right .sticky {
        order: 0;
    }

    .sticky,
    .scrolly {
        display: flex;
        flex-direction: column;
        flex: 1 1; /* Allows growing, shrinking */
    }

    .sticky {
        position: sticky;
        top: 2rem; /* instead of 20vh */
        transform: none; /* remove the translateY */
        padding-top: 1rem; /* optional: ensures h2 has some breathing room */
        z-index: 10;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .scrolly {
        z-index: 1;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: rem 1rem;
            width: 100vw;
        }

        .sticky,
        .scrolly {
            flex: 1 1 auto;
            min-width: 100%;
            position: static; /* remove sticky on mobile */
            transform: none;
        }

        .sticky {
            margin: 2rem;
        }
    }
</style>
