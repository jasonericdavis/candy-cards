<script>
    export let color;
    let flipped = false
    // export let type;
    // export let blocks;
</script>
<style>
    .card {
        height: 300px;
        width: 700px;
        margin: 25px;
        margin-left: auto;
        margin-right: auto;
        perspective: 1000px;
    }

    .flipper {
        position: relative;
        width: 100%;
        height: 100%;
        transition: 0.6s;
        transform-style: preserve-3d;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    }

    /* hide back of pane during swap */
    .front, .back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
    }

    /* front pane, placed above back */
    .front {
        z-index: 2;
        /* for firefox 31 */
        transform: rotateY(0deg);
    }

    /* back, initially hidden pane */
    .back {
        background-color: blue;
        transform: rotateY(180deg);
    }

    .flipper.flipped {
        transform: rotateY(180deg);
    }
</style>

<div class="card"  ontouchstart="this.classList.toggle('hover');" on:click={() => flipped = !flipped}>
    <div class="flipper" class:flipped>
        <div class="front">
            <svg width="200" height="150">
                <rect width="200" height="150" rx="20" ry="20" 
                    style={`fill:${color};stroke:${color};stroke-width:5;opacity:0.8`} />
            </svg>
        </div>
        <div class="back"> This is the back</div>
    </div>
</div>

