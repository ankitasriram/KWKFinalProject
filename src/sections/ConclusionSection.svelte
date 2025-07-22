<script>
    import { fade } from "svelte/transition";
    import { onMount } from "svelte";

    const paragraph = `
    Black homeownership in the Bay Area remains disproportionately low due to ongoing barriers in loan approvals, access to credit, and the lasting effects of redlining. These disparities limit opportunities for wealth-building, access to education, and community investment. Addressing this requires equitable lending practices, inclusive housing policies, and community-driven solutions to break the cycle of systemic inequality.
  `;

    const actions = [
        {
            text: "Workforce Housing Policy",
            link: "https://www.bayareacouncil.org/policy/workforce-housing/",
        },
        {
            text: "SF Family Zoning Reform",
            link: "https://public.govdelivery.com/accounts/CASFPD/subscriber/new?topic_id=CASFPD_369",
        },
        {
            text: "Support Habitat for Humanity",
            link: "https://habitatgsf.org/advancing-black-homeownership/",
        },
        {
            text: "BARHII Housing Toolkit",
            link: "https://barhii.org/black-hat",
        },
    ];

    // State for controlling visibility
    let titleVisible = $state(false);
    let paragraphVisible = $state(false);
    let actionsVisible = $state(false);

    const observerOptions = {
        threshold: 0.1, // Trigger when 10% is visible
        rootMargin: "0px 0px -10% 0px", // Trigger slightly before fully in view
    };

    onMount(() => {
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    const target = entry.target;

                    if (target.classList.contains("fade-title")) {
                        titleVisible = true;
                    } else if (target.classList.contains("fade-paragraph")) {
                        paragraphVisible = true;
                    } else if (target.classList.contains("fade-actions")) {
                        actionsVisible = true;
                    }
                }
            });
        }, observerOptions);

        // Observe elements after a short delay to ensure they're rendered
        setTimeout(() => {
            const titleElement = document.querySelector(".fade-title");
            const paragraphElement = document.querySelector(".fade-paragraph");
            const actionsElement = document.querySelector(".fade-actions");

            if (titleElement) observer.observe(titleElement);
            if (paragraphElement) observer.observe(paragraphElement);
            if (actionsElement) observer.observe(actionsElement);
        }, 100);

        return () => {
            observer.disconnect();
        };
    });
</script>

<section class="page">
    <div class="fade-title">
        {#if titleVisible}
            <h2 in:fade={{ duration: 800, delay: 100 }}>In Conclusion</h2>
        {:else}
            <h2 style="opacity: 0;">In Conclusion</h2>
        {/if}
    </div>

    <div class="fade-paragraph">
        {#if paragraphVisible}
            <p in:fade={{ duration: 1000, delay: 200 }}>{@html paragraph}</p>
        {:else}
            <p style="opacity: 0;">{@html paragraph}</p>
        {/if}
    </div>

    <div class="fade-actions">
        {#if actionsVisible}
            <div in:fade={{ duration: 1200, delay: 300 }}>
                <h3>Take Action</h3>
                <div class="button-group">
                    {#each actions as action, i}
                        <a
                            href={action.link}
                            target="_blank"
                            rel="noopener noreferrer"
                            class="button"
                            style="animation-delay: {400 + i * 100}ms;"
                        >
                            {action.text}
                        </a>
                    {/each}
                </div>
            </div>
        {:else}
            <div style="opacity: 0;">
                <h3>Take Action</h3>
                <div class="button-group">
                    {#each actions as action}
                        <a
                            href={action.link}
                            target="_blank"
                            rel="noopener noreferrer"
                            class="button"
                        >
                            {action.text}
                        </a>
                    {/each}
                </div>
            </div>
        {/if}
    </div>
</section>

<style>
    .page {
        background-color: #fffeed;
        padding: 6rem 2rem;
        box-sizing: border-box;
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-family: "Merriweather", serif;
        color: rgb(3, 73, 109);
        width: 100%;
    }

    h2 {
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

    h3 {
        font-family: "DM Serif Text", serif;
        font-style: italic;
        font-size: clamp(1.5rem, 7vw, 8rem);
        line-height: clamp(4.5rem, 9vw, 13rem);
        text-align: center;
        color: #024364;
        margin-top: 2rem;
        margin-bottom: 1rem;
        text-shadow: 4px 4px 6px rgba(108, 138, 153, 0.472);
    }

    p {
        max-width: 60ch;
        font-size: 1.2rem;
        line-height: 1.6;
        margin: 0 auto 4rem auto; /* center block with margin bottom */
        text-align: center; /* just in case */
    }

    .button-group {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 1rem;
        max-width: 60ch;
        margin: 0 auto; /* center the button container */
    }

    :global(p strong) {
        font-weight: 700;
    }

    .button {
        background-color: rgb(3, 73, 109);
        color: #fffeed;
        padding: 0.6rem 1.2rem;
        font-size: 1.5rem;
        font-weight: 600;
        border-radius: 5px;
        text-decoration: none;
        white-space: nowrap;
        transition: background-color 0.3s ease;
        box-shadow: 0 2px 5px rgba(3, 73, 109, 0.3);
        opacity: 0;
        animation: fadeInButton 0.6s ease-out forwards;
    }

    .button:hover,
    .button:focus {
        background-color: #012d4a;
        box-shadow: 0 4px 10px rgba(1, 45, 74, 0.6);
    }

    @keyframes fadeInButton {
        from {
            opacity: 0;
            transform: translateY(10px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* Preserve layout space */
    .fade-title,
    .fade-paragraph,
    .fade-actions {
        width: 100%;
    }
</style>
