<script>
    export let borderColor = "#ccc";
    export let backgroundColor = "#fff";
    export let width = "50%";
    export let height = "auto";
    export let text = "";
    export let textColor = "#000";
    export let padding = "1rem";
    export let borderRadius = "8px";
</script>

<div
    class="textbox"
    style="
    border: 2px solid {borderColor};
    background-color: {backgroundColor};
    width: {width};
    height: {height};
    padding: {padding};
    border-radius: {borderRadius};
    color: {textColor};
  "
>
    <slot>{text}</slot>
</div>

<style>
    .textbox {
        box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
        font-family: "Merriweather", serif;
        
    }
</style>
