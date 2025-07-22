<!-- ScrollTextChartSection.svelte -->
<script>
    import { onMount } from "svelte";
    import BarriersBarChart from "../lib/BarriersBarChart.svelte";
    import TextBox from "../lib/TextBox.svelte";

    export let categories;
    export let series;
    export let textBoxes = [];

    let currentStep = 0;

    function handleScroll(event) {
        const steps = document.querySelectorAll(".scroll-step");
        let index = 0;
        for (let i = 0; i < steps.length; i++) {
            const rect = steps[i].getBoundingClientRect();
            if (rect.top < window.innerHeight * 0.5) {
                index = i;
            }
        }
        currentStep = index;
    }

    onMount(() => {
        window.addEventListener("scroll", handleScroll);
        return () => window.removeEventListener("scroll", handleScroll);
    });
</script>

<div class="scrolly-section">
    <!-- Left (sticky chart) -->
    <div class="sticky-left">
        <BarriersBarChart
            title="Application Denials by Race (2024)"
            {categories}
            {series}
        />
    </div>

    <!-- Right (scrolling text) -->
    <div class="scroll-right">
        {#each textBoxes as tb, i}
            <div class="scroll-step">
                <TextBox
                    text={tb}
                    borderColor="#fff397"
                    backgroundColor="#063244"
                    textColor="#ffffff"
                    width="100%"
                    padding="1.25rem"
                    borderRadius="12px"
                />
            </div>
        {/each}
    </div>
</div>

<style>
    .scrolly-section {
        display: flex;
        height: 100vh;
        position: relative;
        padding: 1rem;
        gap: 2rem;
    }

    .sticky-left {
        position: sticky;
        top: 0;
        flex: 1;
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .scroll-right {
        flex: 1;
        display: flex;
        flex-direction: column;
        gap: 4rem;
        overflow: visible;
        padding-top: 10vh;
        padding-bottom: 100vh; /* ensures last text scrolls before switching */
    }

    .scroll-step {
        min-height: 60vh;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>
