<script>
    import { slide } from "svelte/transition";
    let visible = false;
    let visible_2 = false;
    function collapse_top() {
        visible = !visible;
    }
    function collapse_top2() {
        visible_2 = !visible_2;
    }
</script>

<ul>
    <li>
        <span on:click={collapse_top}>Click me</span>
        {#if visible}
            <ul transition:slide class="buggy-height">
                <li>
                    <span on:click={collapse_top2}>Click me 2</span>
                    {#if visible_2}
                        <ul transition:slide|local>
                            <li>Menu inner inner 1</li>
                            <li>Menu inner inner 2</li>
                            <li>Menu inner inner 3</li>
                        </ul>
                    {/if}
                </li>
                <li>Menu item inner 2</li>
                <li>Menu item inner 3</li>
            </ul>
        {/if}
    </li>
    <li>Menu item 2</li>
    <li>Menu item 3</li>
</ul>

<style>
    ul {
        list-style: none;
        user-select: none;
    }
    .buggy-height {
        background-color: salmon;
    }

    span {
        cursor: pointer;
    }
</style>
