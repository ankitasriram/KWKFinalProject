<script>
    import BarriersBarChart from "../lib/BarriersBarChart.svelte";
    import Scroller from "../lib/Scroller.svelte";
    import TextBox from "../lib/TextBox.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const raceCategories = [
        "White",
        "Asian",
        "Black or African American",
        "Hispanic or Latino",
    ];

    const raceColors = {
        White: "#cc9e78",
        Asian: "#8fb6c9",
        "Black or African American": "#bd1906",
        "Hispanic or Latino": "#d0a8ed",
    };

    const applicationDenialsSeries = [
        {
            name: "Application denied",
            data: raceCategories.map((race, i) => ({
                name: race,
                y: [0.51, 0.56, 0.65, 0.49][i],
                color: raceColors[race],
            })),
        },
    ];

    const conventionalLoansSeries = [
        {
            name: "Loan originated (Conventional)",
            data: raceCategories.map((race, i) => ({
                name: race,
                y: [2.46, 3.17, 1.49, 1.52][i],
                color: raceColors[race],
            })),
        },
    ];

    const fhaLoansSeries = [
        {
            name: "Loan originated (FHA)",
            data: raceCategories.map((race, i) => ({
                name: race,
                y: [0.34, 0.21, 0.57, 0.44][i],
                color: raceColors[race],
            })),
        },
    ];

    const loanOriginatedSeries = [
        {
            name: "Loan originated (All types)",
            data: raceCategories.map((race, i) => ({
                name: race,
                y: [1.86, 2.0, 1.08, 1.06][i],
                color: raceColors[race],
            })),
        },
    ];
</script>

<h1>Barriers</h1>

<!-- First Scroller: Application Denials -->
<div class="scrolly-wrapper">
    <Scroller layout="right" backgroundColor="#024364">
        {#snippet sticky()}
            <h2>Loan Application Denials by Race (2024)</h2>
            <BarriersBarChart
                title="Application Denials by Race (2024)"
                categories={raceCategories}
                series={applicationDenialsSeries}
            />
        {/snippet}

        {#snippet scrolly()}
            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="100%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    Black and Hispanic applicants face significantly higher
                    denial rates compared to white and Asian applicants. For
                    every 100 adults, about 0.65 Black and 0.56 Hispanic
                    applicants are denied, compared to 0.51 white and 0.49 Asian
                    applicants. These disparities suggest persistent systemic
                    barriers in the mortgage approval process.
                </p>
            </ArticleText>

            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="100%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    While the denial rates may appear numerically small, they
                    represent real barriers that compound over time. For Black
                    and Hispanic households especially, higher denial rates
                    reduce opportunities for homeownership, wealth-building, and
                    neighborhood mobility—critical levers for generational
                    advancement.
                </p>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<!-- Second Scroller: Conventional and FHA Loans Side by Side -->
<div class="scrolly-wrapper">
    <Scroller layout="left" backgroundColor="#024364">
        {#snippet sticky()}
            <div class="side-by-side-charts">
                <div class="chart-section">
                    <h2>Conventional Loans by Race</h2>
                    <div class="chart-wrapper">
                        <BarriersBarChart
                            title="Conventional Loans by Race (2024)"
                            categories={raceCategories}
                            series={conventionalLoansSeries}
                        />
                    </div>
                </div>

                <div class="chart-section">
                    <h2>FHA Loans by Race</h2>
                    <div class="chart-wrapper">
                        <BarriersBarChart
                            title="FHA Loans by Race (2024)"
                            categories={raceCategories}
                            series={fhaLoansSeries}
                        />
                    </div>
                </div>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="87.5%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    Conventional loans show stark disparities across racial
                    lines. White and Asian applicants receive conventional loans
                    at rates of 2.46 and 3.17 per 100 adults respectively, while
                    Black and Hispanic applicants receive them at much lower
                    rates of 1.49 and 1.52 per 100 adults.
                </p>
            </ArticleText>

            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="87.5%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    FHA loans, designed to increase homeownership access, show a
                    different pattern. Black applicants have the highest FHA
                    loan origination rate at 0.57 per 100 adults, suggesting
                    these government-backed loans serve as a critical pathway
                    for communities facing barriers in conventional lending.
                </p>
            </ArticleText>

            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="87.5%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    The contrasting patterns between conventional and FHA loans
                    reveal how different lending mechanisms serve different
                    communities. While conventional loans favor higher-income
                    borrowers, FHA loans provide essential access for first-time
                    and lower-income homebuyers, particularly in communities of
                    color.
                </p>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<!-- Third Scroller: All Loan Types -->
<div class="scrolly-wrapper">
    <Scroller layout="right" backgroundColor="#024364">
        {#snippet sticky()}
            <h2>All Loan Types by Race (2024)</h2>
            <BarriersBarChart
                title="All Loan Types by Race (2024)"
                categories={raceCategories}
                series={loanOriginatedSeries}
            />
        {/snippet}

        {#snippet scrolly()}
            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="100%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    When examining all loan types combined, the disparities
                    become even more apparent. White and Asian applicants
                    receive loans at rates of 1.86 and 2.0 per 100 adults
                    respectively, while Black and Hispanic applicants receive
                    them at significantly lower rates of 1.08 and 1.06 per 100
                    adults.
                </p>
            </ArticleText>

            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="100%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    Despite lower denial rates, conventional and FHA loans
                    remain unevenly distributed across racial lines,
                    underscoring persistent inequities in access to favorable
                    mortgage terms. These patterns reflect broader systemic
                    barriers that limit wealth-building opportunities for
                    communities of color.
                </p>
            </ArticleText>

            <ArticleText
                borderColor="#fff397"
                backgroundColor="#063244"
                textColor="#fff"
                padding="1.25rem"
                borderRadius="12px"
                width="100%"
                boxShadowColor="rgba(255, 255, 0, 0.3)"
            >
                <p>
                    The cumulative effect of these lending disparities extends
                    beyond individual transactions. Lower loan origination rates
                    for Black and Hispanic families translate to reduced
                    homeownership opportunities, limiting their ability to build
                    generational wealth and access better schools and
                    neighborhoods.
                </p>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    :global(body, html) {
        margin: 0;
        padding: 0;
        height: 110%;
        background: #024364;
    }

    .screen {
        height: 100vh;
        width: 100vw;
        background-color: black;
        position: relative;
    }

    .scrolly {
        z-index: 1;
        background-color: var(--scrolly-bg, transparent);
        padding: 2rem;
    }

    /* Wrapper styling for consistent margins */
    .scrolly-wrapper {
        margin: 0 2rem;
    }

    /* Side-by-side charts styling */
    .side-by-side-charts {
        display: flex;
        gap: 2rem;
        width: 100%;
        max-width: 800px; /* Constrain overall width */
        height: 100%;
        align-items: stretch;
        margin-right: 3rem; /* Add space between charts and scrolling text */
    }

    .chart-section {
        flex: 1;
        display: flex;
        flex-direction: column;
        min-height: 500px;
        max-width: 380px; /* Constrain individual chart width */
    }

    .chart-wrapper {
        flex: 1;
        width: 100%;
        max-width: 100%; /* Prevent overflow */
    }

    /* Responsive: stack charts on mobile */
    @media (max-width: 768px) {
        .scrolly-wrapper {
            margin: 0 1rem; /* Reduce margins on mobile */
        }

        .side-by-side-charts {
            flex-direction: column;
            gap: 1rem;
            margin-right: 0; /* Remove extra margin on mobile */
        }

        .chart-section {
            min-height: 300px;
        }
    }

    h1 {
        font-family: "DM Serif Text", serif;
        font-style: italic;
        font-size: clamp(1.5rem, 9vw, 9rem);
        line-height: clamp(4.5rem, 9vw, 13rem);
        text-align: center;
        color: #fffeed;
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
        color: #fff397;
        text-align: center;
    }

    p {
        font-size: 1.5rem;
        font-family: "Merriweather", serif;
    }
</style>
