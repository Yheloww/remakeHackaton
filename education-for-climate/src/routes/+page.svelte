<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut } from 'svelte/easing';

    let width = 1000;
    let height = 500;

    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width/5]);

    let data = [
    {name:"Bruxelles",step1:100, step2:97, step3:83, step4:3.5},
    {name:"wallonie",step1:110, step2:100, step3:85.7, step4:3.6},
    {name:"Flandre",step1:110, step2:110, step3:100, step4:4.2},
    {name:"total",step1:110, step2:110, step3:110, step4:100}
    ];

    const tweenedX = tweened(data.map((d) => d.step1),{
        duration: 800,
        easing: cubicOut
    });

    const step2 = function () {
        tweenedX.set(data.map((d) => d.step2));
        d3.selectAll('rect').attr("transform", "translate(-100, 0)");
    };

    const step3 = function () {
        tweenedX.set(data.map((d) => d.step3))
    };

    const step4 = function () {
        tweenedX.set(data.map((d) => d.step4))
    };

    const step1 = function () {
        tweenedX.set(data.map((d) => d.step1))
    };
</script>

<section>
    <div class="container" bind:clientWidth={width}>
        <svg {height} {width}>
            {#each data as circle, index}
            <circle 
            cx={width/2} 
            cy=250
            r={xScale($tweenedX[index])} 
            fill="none" 
            stroke={ $tweenedX[index] >= 100 ? "green" : "black"}
            stroke-width={ $tweenedX[index] > 108 ? "0px" : "2px"}/>
            <rect class="sticker" x={width/4} y={250 - 25} width="100" height="50" fill="green"/>
            {/each}
        </svg>
    </div>
<div class="button">
    <button class="btn-1" on:click={step1}>Step 1</button>
    <button class="btn-2" on:click={step2}>Step 2</button>
    <button class="btn-3" on:click={step3}>Step 3</button>
    <button class="btn-4" on:click={step4}>Step 4</button>

</div>
</section>


<style>
    .container {
        background: whitesmoke;
        box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
        top: 10%;
        margin: 0 auto;
    }	

    .sticker {
        border-radius: 5px;
    }
</style>