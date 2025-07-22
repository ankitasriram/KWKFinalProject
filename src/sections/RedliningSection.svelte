<script>
    import { fade, fly } from "svelte/transition";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    const map3 = "/SFBlackPop.png";
    const map4 = "/SFHomeowner.png";

    let currentMap = $state("");

    const options = {
        threshold: [0.85, 0.95],
    };

    const showMap3Callback = (entries, observer) => {
        entries.forEach((entry) => {
            if (entry.intersectionRatio >= 0.9) {
                currentMap = "map3";
            }
        });
    };

    const showMap4Callback = (entries, observer) => {
        entries.forEach((entry) => {
            if (entry.intersectionRatio >= 0.9) {
                currentMap = "map4";
            }
        });
    };

    const hideMapCallback = (entries, observer) => {
        entries.forEach((entry) => {
            if (entry.intersectionRatio >= 0.9) {
                currentMap = "";
            }
        });
    };
</script>

<div class="page-wrapper">
    <h1>Redlining</h1>

    <div class="content-container">
        <Scroller layout="left" backgroundColor="#024364">
            {#snippet sticky()}
                <div class="sticky-image-container">
                    {#if currentMap === "map3"}
                        <img
                            src={map3}
                            alt="Map 3 - Black Population in San Francisco"
                            class="map-image"
                            in:fly={{ x: -200, duration: 800 }}
                            out:fade={{ duration: 400 }}
                        />
                        <p class="map-caption-sticky">
                            Map 3 – Black Population in San Francisco
                        </p>
                    {:else if currentMap === "map4"}
                        <img
                            src={map4}
                            alt="Map 4 - Homeownership in San Francisco"
                            class="map-image"
                            in:fly={{ x: -200, duration: 800 }}
                            out:fade={{ duration: 400 }}
                        />
                        <p class="map-caption-sticky">
                            Map 4 – Homeownership in San Francisco
                        </p>
                    {/if}
                </div>
            {/snippet}

            {#snippet scrolly()}
                <ObservedArticleText
                    callback={showMap3Callback}
                    {options}
                    borderColor="#fff397"
                    backgroundColor="#024364"
                    textColor="#fff397"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="100%"
                    boxShadowColor="rgba(255, 243, 151, 0.3)"
                >
                    <h2>Black Population Distribution</h2>
                    <p>
                        This map shows the distribution of Black residents in
                        San Francisco. The concentration patterns reveal how
                        redlining practices created distinct residential
                        boundaries that limited where Black families could live
                        and build wealth through homeownership.
                    </p>
                </ObservedArticleText>

                <ObservedArticleText
                    callback={showMap4Callback}
                    {options}
                    borderColor="#fff397"
                    backgroundColor="#024364"
                    textColor="#fff397"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="100%"
                    boxShadowColor="rgba(255, 243, 151, 0.3)"
                >
                    <h2>Homeownership Patterns</h2>
                    <p>
                        The homeownership map reveals the stark disparities
                        created by discriminatory lending practices. Areas that
                        were redlined show significantly lower rates of
                        homeownership, demonstrating how these policies
                        prevented wealth accumulation in affected communities.
                    </p>
                </ObservedArticleText>

                <ObservedArticleText
                    callback={hideMapCallback}
                    {options}
                    borderColor="#fff397"
                    backgroundColor="#024364"
                    textColor="#fff397"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="100%"
                    boxShadowColor="rgba(255, 243, 151, 0.3)"
                >
                    <h2>Lasting Impact</h2>
                    <p>
                        The legacy of redlining extends far beyond historical
                        boundaries. These discriminatory practices created
                        wealth gaps, limited access to quality education and
                        healthcare, and perpetuated residential segregation that
                        continues to affect San Francisco communities today.
                        Understanding this history is crucial for addressing
                        ongoing housing inequities.
                    </p>
                </ObservedArticleText>
            {/snippet}
        </Scroller>
    </div>
</div>

<style>
    /* Page wrapper with dark blue background */
    .page-wrapper {
        min-height: 100vh;
        background: #024364;
        padding: 0;
    }

    .content-container {
        padding: 0 2rem;
    }
    h1 {
        font-family: "DM Serif Text", serif;
        font-style: italic;
        font-size: clamp(1.5rem, 9vw, 9rem);
        line-height: clamp(4.5rem, 9vw, 13rem);
        text-align: center;
        color: #fff397;
        margin-top: 2rem;
        margin-bottom: 1rem;
        text-decoration: underline;
        text-decoration-color: rgba(220, 38, 38, 1);
        text-decoration-thickness: 4px;
        text-underline-offset: 8px;
        text-shadow:
            1px 1px 0px rgba(0, 75, 100, 0.8),
            -1px -1px 0px rgba(0, 75, 100, 0.8),
            1px -1px 0px rgba(0, 75, 100, 0.8),
            -1px 1px 0px rgba(0, 75, 100, 0.8),
            3px 3px 0px rgba(220, 38, 38, 1),
            6px 6px 8px rgba(0, 0, 0, 0.8);
    }

    .sticky-image-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        width: 100%;
        padding: 0;
        margin: 0;
    }

    .map-image {
        width: 100%;
        height: 85vh;
        border: none;
        border-radius: 0;
        box-shadow: none;
        object-fit: contain;
    }

    .map-caption-sticky {
        font-family: "Merriweather", serif;
        font-style: italic;
        color: #fff397;
        opacity: 0.8;
        margin-top: 1rem;
        font-size: 0.9rem;
        text-align: center;
    }

    h2 {
        font-family: "Merriweather", serif;
        font-weight: 600;
        font-size: 1.75rem;
        margin-bottom: 0.5rem;
        color: #fff397;
    }

    p {
        font-family: "Merriweather", serif;
        font-size: 1.5rem;
        line-height: 1.6;
        color: white;
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
        .content-container {
            padding: 0 1rem;
        }

        h1 {
            margin-top: 1rem;
        }

        .map-image {
            max-width: 90%;
            max-height: 60vh;
        }
    }
</style>
