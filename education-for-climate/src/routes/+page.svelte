<script>
    import data from "../data/data";
    import * as d3 from 'd3'

    console.log(data); 

    let width = 1000;
    let height = 1000;

    const xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width/4]);

</script>
<div class="container" bind:clientWidth={width} bind:clientHeight={height}>
    <svg {height} {width}>
        {#each data as circle}
        <circle cx={width/2} cy=400 r={xScale(circle.pourcentage)} fill="none" stroke="black"/>
        {/each}
    </svg>
</div>


<style>
    .container {
        margin: 0 auto;
    }
   
</style>