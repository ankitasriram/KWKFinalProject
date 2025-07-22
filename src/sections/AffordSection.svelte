<script>
    import HVIChart from "../lib/HVIChart.svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div class="page-wrapper">
    <h1>Afford</h1>

    <!-- First Scroller: HVI Chart -->
    <div class="scrolly-wrapper">
        <Scroller layout="right" backgroundColor="#FFFEED">
            {#snippet sticky()}
                <h2>Housing Value Index by Race</h2>
                <div class="chart-wrapper">
                    <HVIChart />
                </div>
            {/snippet}

            {#snippet scrolly()}
                <ArticleText
                    borderColor="#024364"
                    backgroundColor="#fff397"
                    textColor="#024364"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="100%"
                    boxShadowColor="rgba(2, 67, 100, 0.3)"
                >
                    <p>
                        Housing affordability varies dramatically across racial
                        lines, with systemic barriers creating significant
                        disparities in homeownership opportunities. These
                        differences reflect decades of discriminatory lending
                        practices and wealth gaps that continue to impact
                        communities today.
                    </p>
                </ArticleText>

                <ArticleText
                    borderColor="#024364"
                    backgroundColor="#fff397"
                    textColor="#024364"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="100%"
                    boxShadowColor="rgba(2, 67, 100, 0.3)"
                >
                    <p>
                        The Housing Value Index reveals how different
                        communities experience vastly different barriers to
                        homeownership. Higher values indicate greater difficulty
                        in accessing affordable housing options within their
                        local markets.
                    </p>
                </ArticleText>
            {/snippet}
        </Scroller>
    </div>

    <!-- Second Scroller: California Homeownership Rates -->
    <div class="scrolly-wrapper">
        <Scroller layout="left" backgroundColor="#FFFEED">
            {#snippet sticky()}
                <h2>Homeownership Rates by Race in California</h2>
                <div class="chart-wrapper">
                    <img
                        src={`${import.meta.env.BASE_URL}HO-CA.jpg`}
                        alt="Homeownership Rates by Race in California Chart"
                        class="homeownership-image"
                    />
                </div>
            {/snippet}

            {#snippet scrolly()}
                <ArticleText
                    borderColor="#024364"
                    backgroundColor="#fff397"
                    textColor="#024364"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="87.5%"
                    boxShadowColor="rgba(2, 67, 100, 0.3)"
                >
                    <p>
                        California's homeownership rates reveal stark racial
                        disparities that persist despite decades of civil rights
                        legislation. White families achieve homeownership at
                        rates significantly higher than Black, Hispanic, and
                        other communities of color.
                    </p>
                </ArticleText>

                <ArticleText
                    borderColor="#024364"
                    backgroundColor="#fff397"
                    textColor="#024364"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="87.5%"
                    boxShadowColor="rgba(2, 67, 100, 0.3)"
                >
                    <p>
                        The homeownership gap in California is particularly
                        pronounced for Black residents, who face the greatest
                        challenges in accessing homeownership. This disparity
                        represents not just individual hardship, but systemic
                        barriers that limit wealth accumulation and community
                        investment opportunities.
                    </p>
                </ArticleText>

                <ArticleText
                    borderColor="#024364"
                    backgroundColor="#fff397"
                    textColor="#024364"
                    padding="1.25rem"
                    borderRadius="12px"
                    width="87.5%"
                    boxShadowColor="rgba(2, 67, 100, 0.3)"
                >
                    <p>
                        These patterns reflect the compounding effects of
                        historical redlining, discriminatory lending practices,
                        and ongoing wealth gaps. Addressing California's
                        homeownership disparities requires targeted
                        interventions that recognize the unique challenges
                        facing each community.
                    </p>
                </ArticleText>
            {/snippet}
        </Scroller>
    </div>
</div>

<style>
    :global(body, html) {
        margin: 0;
        padding: 0;
        height: 100%;
        /* Removed global background color */
    }

    /* Page wrapper with background color scoped to this component */
    .page-wrapper {
        min-height: 100vh;
        background: #fff397;
    }

    /* Wrapper styling for consistent margins */
    .scrolly-wrapper {
        margin: 0 2rem;
    }

    .chart-wrapper {
        width: 100%;
        max-width: 600px; /* Constrain chart width */
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .homeownership-image {
        width: 120%;
        height: 800px;
        border-radius: 12px;
        object-fit: contain;
        background-color: rgba(255, 255, 255, 0.1);
    }

    h1 {
        font-family: "DM Serif Text", serif;
        font-style: italic;
        font-size: clamp(1.5rem, 9vw, 9rem);
        line-height: clamp(4.5rem, 9vw, 13rem);
        text-align: center;
        color: #024364;
        margin-top: 2rem;
        margin-bottom: 1rem;
        text-shadow: 4px 4px 6px rgba(108, 138, 153, 0.8);
    }

    h2 {
        font-family: "Merriweather", serif;
        font-style: bold;
        font-size: 1.75rem;
        font-weight: 600;
        margin: 1rem 0;
        color: #024364;
        text-align: center;
    }

    p {
        font-size: 1.5rem;
        font-family: "Merriweather", serif;
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
        .scrolly-wrapper {
            margin: 0 1rem;
        }

        .homeownership-image {
            height: 400px;
        }

        .chart-wrapper {
            max-width: 100%;
        }
    }
</style>
