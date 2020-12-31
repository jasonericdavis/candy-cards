<script>
    import { slide } from 'svelte/transition';
    export let color;
    export let clickHandler;
</script>
<style>
    .block-container {
        margin-left: auto;
        margin-right: auto;
    }

    .block {
        width: 200px;
        height: 200px;

        background: var(--block-color);
        box-shadow: inset 5px 10px 5px 3px rgba(0, 0, 0, 0.25);
        border-radius: 25px;
        margin-left: auto;
        margin-right: auto;
        
    }

    .card2 {
        width: 500px;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        margin-left: auto;
        margin-right: auto;
        padding-top: 20px;
        padding-bottom: 20px;
    }
</style>

<div on:click={clickHandler}  transition:slide="{{delay: 250, duration: 1000}}">
    <div class="card2" style={`--block-color: ${color};`}>
         <div class="block" />
    </div>
</div>

