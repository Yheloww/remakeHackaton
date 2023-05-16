<script>
    import AxisX from "../components/AxisX.svelte";
    import AxisY from "../components/AxisY.svelte";
    import Tooltip from "../components/tooltip.svelte";
    import { each } from "svelte/internal";
    import data from "../data/data";
    import * as d3 from 'd3'
    // import {scaleLinear} from "d3-scale";

    let width = 400;
    let height= 400;

    const margin = { top:20, right:40, left:0, bottom:20};

    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width - margin.left - margin.right])

    const yScale = d3.scaleLinear()
    .domain([0,d3.max(data, d => d.hours)])
    .range([height - margin.top - margin.bottom,0])

    let hoverData;
    $: console.log(hoverData);

</script>

<h1> Study longer , score better !</h1>
<div class="chart-container" 
     bind:clientWidth={width}
     on:mouseleave={ () => {
        hoverData = null;
     }}>
<svg {width} {height}>
    <AxisX height={height} xScale={xScale} {margin}/>
    <AxisY {width} {yScale} {margin}/>
    <g class='circles' transform="translate({margin.left} {margin.top})">
    {#each data.sort((a,b) => a.grade - b.grade) as student}
    <circle cx={xScale(student.grade)} 
            cy={yScale(student.hours)} 
            r={hoverData && hoverData == student ? "20":"10"}
            opacity={hoverData ? hoverData == student ? "1":".5":"1"}
            fill="aquamarine"
            stroke="aqua"
            on:mouseover={ () => {
                hoverData = student;
                }}
            on:focus={ () => {
                hoverData = student;
                }}
            tabIndex="0"                
            />
    {/each}
    </g>
</svg>
</div>
    {#if hoverData}
    <Tooltip  data={hoverData} {xScale} {yScale}/>
    {/if}



<style>
    * {
        font-family: sans-serif;
    }
    circle {
        transition: r 300ms ease, opacity 300ms ease;
        cursor: pointer;
    }

    circle:focus {
        outline: none;
    }

    h1 {
        font-size: 1.5rem;
        font-weight: 600;
        margin-bottom: 0.5rem;
    }
</style>