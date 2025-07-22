<script>
    export let borderColor = "#8427c9";
    export let backgroundColor = "#ff99fc";
    export let textColor = "#007052";
    export let padding = "20px";
    export let borderRadius = "20px";
    export let width = "50%";
    export let boxShadowColor = "#8aa6df";
</script>

<div
    class="article-text"
    style="
    --border-color: {borderColor};
    --bg-color: {backgroundColor};
    --text-color: {textColor};
    --padding: {padding};
    --radius: {borderRadius};
    --width: {width};
    --shadow-color: {boxShadowColor};
  "
>
    <slot />
</div>

<style>
    .article-text {
        border-color: var(--border-color);
        background-color: var(--bg-color);
        color: var(--text-color);
        padding: var(--padding);
        border-radius: var(--radius);
        width: var(--width);
        box-shadow: 16px 16px var(--shadow-color);
        border-style: solid;
        border-width: 3px;
        box-sizing: border-box;
        margin: 50vh auto;
        position: relative; /* allow layering */
        z-index: 10;
    }
</style>
