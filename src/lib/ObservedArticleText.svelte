<script>
    import { onMount } from "svelte";

    let { children, callback, options } = $props();

    // this uniqueId just lets us target the element
    // with `document.getElementById(uniqueId)` later on.
    // it's a little hacky, but it works.
    let uniqueId = Math.random().toString();

    // here we define the onMount() function for this component.
    // svelte handles calling the onMount() function *after* all of the HTML in this
    // component has been mounted to the DOM. we have to put the intersection observer
    // stuff in onMount() because we need to target the <div> we create below,
    // but it won't actually exist in the DOM until it's been mounted.
    onMount(() => {
        let intersectionObserver = new IntersectionObserver(callback, options);

        const observedElement = document.getElementById(uniqueId);
        intersectionObserver.observe(observedElement);
    });
</script>

<!-- assign the containing div the id `uniqueId` so we can target it -->
<div id={uniqueId} class="article-text">
    <div class="content">
        {@render children()}
    </div>
</div>

<style>
    .article-text {
        margin: 50vh auto;
        width: 50%;
        background-color: #026ca1;
        border: solid #fff397 3px;
        border-radius: 20px;
        padding: 20px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    }

    .content :global(h2) {
        color: #fffeed;
        margin-bottom: 1rem;
    }

    .content :global(p) {
        color: #fff397;
        line-height: 1.6;
    }
</style>
