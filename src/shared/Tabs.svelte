<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    export let tabs;
    export let activeTab;

</script>

<div class="tabs">
    <ul>
        {#each tabs as tab}
            <li on:click={() => dispatch('tabChange', tab)}>
                <div class:active={tab === activeTab}>{tab}</div>
            </li>
        {/each}
    </ul>

    <!-- /* colors
#595354
#9F7178
#E5CCBF
#766273
#513F55
#6ea4bf
#73fbd3
#e6c79c
#c68866
#087ca7
 */ -->
</div>

<style>
    .tabs {
        margin-bottom: 40px;
    }
    ul {
        display: flex;
        justify-content: center;
        padding: 0;
        list-style-type: none;
    }
    li {
        margin: 0 16px;
        font-size: 18px;
        color: #b18fcf;
        cursor: pointer;
    }
    .active {
        color: #087ca7;
        border-bottom: 2px solid #087ca7;
        padding-bottom: 8px;
    }
</style>
