<script>
    export let data;
    export let xScale;
    export let yScale;
</script>
<div class="tooltip" style="position:absolute;
    top: {yScale(data.hours)}px;
    left: {xScale(data.grade)}px">
    <div>
        <p>{data.name} </p>
    </div>
    <div>
        <p>{data.hours} hours studied</p> 
    </div>
</div>

<style>
    .tooltip {
        padding-left: 5px;
        padding-right: 5px;
        background-color: white;
        pointer-events: none;
        transition: top 300ms ease, left 300ms ease;
        border-radius: 5px;
        box-shadow: 2px 2px 2px 2px rgba(0,0,0,.3);
        font-size: 0.9rem;
    }
    

</style>