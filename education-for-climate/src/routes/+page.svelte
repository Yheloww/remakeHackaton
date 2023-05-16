<script>
    import data from "../data/data";
    import * as d3 from 'd3'

    console.log(data); 

    let width = 1000;
    let height = 1000;

    const xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,200]);

</script>

<svg {height} {width}>
    {#each data as circle}
    <circle cx="250" cy="250" r={xScale(circle.pourcentage)} fill="none" stroke="black"/>
    {/each}
</svg>


<style>
   
</style>