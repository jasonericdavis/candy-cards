<script>
    export let card;
</script>
<style>

    .block {
        width: 200px;
        height: 200px;

        background: var(--block-color);
        box-shadow: inset 5px 10px 5px 3px rgba(0, 0, 0, 0.25);
        border-radius: 25px;
        margin-left: auto;
        margin-right: auto;
        
    }

    span {
        background-color: #C4C4C4;
        color: var(--card-color);
        padding: 2px 10px;
        letter-spacing: 7px;
    }

    span.orange {
        background-color: #686868;
    }

</style>

<div class="card" style={`--block-color: var(--block-color-${card.color}); max-width: 500px`}>
    
    {#if card.blocks > 1}
        <div style={'display: flex'}>
            <div class="block" style={`width: 200px`}/>
            <div class="block" style={`width: 200px`}/>
        </div>
    {:else}
        <div class="block" style={`width: 200px`}/>
    {/if}
    <p>
        Move to the {(card.blocks > 1)? 'second': 'next'}
        <span class={card.color} style={`--card-color: ${card.color}`}>{card.color}</span>
        block
    </p>
</div>

