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
        <span on:click={collapse_top}>0.1 - Click me</span>
        {#if visible}
            <ul transition:slide class="buggy-height">
                <li>
                    <span on:click={collapse_top2}>1.1 - Click me 2</span>
                    {#if visible_2}
                        <ul transition:slide|local>
                            <li>2.1</li>
                            <li>2.1</li>
                            <li>2.1</li>
                        </ul>
                    {/if}
                </li>
                <li>1.2</li>
                <li>1.3</li>
            </ul>
        {/if}
    </li>
    <li>0.2</li>
    <li>0.3</li>
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
