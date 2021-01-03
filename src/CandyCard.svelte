<script>
    export let card;
</script>
<style>
    .block {
        width: 200px;
        height: 200px;

        background: var(--block-color);
        /* box-shadow: inset 5px 10px 5px 3px rgba(0, 0, 0, 0.25); */
        border-radius: 25px;
        margin-left: auto;
        margin-right: auto;
        
    }

    img {
        height: 100%;
    }
</style>

<div class="card" style={`--block-color: transparent; max-width: 500px`}>
    <div class="block">
        <img src={card.url} alt={card.name}/>
    </div>
    <p>
        Move to the {card.name} block
    </p>
</div>