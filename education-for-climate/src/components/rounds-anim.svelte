<script>
    import * as d3 from 'd3'
    import { tweened } from "svelte/motion";
    import { cubicOut} from 'svelte/easing';
    import {fade} from 'svelte/transition';

    let width = 1000;
    let height = 1000;


    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width/5]);

    let data = [
    {name:"Bruxelles",step1:100, step2:97, step3:83, step4:3.5},
    {name:"wallonie",step1:120, step2:100, step3:85.7, step4:3.6},
    {name:"Flandre",step1:120, step2:120, step3:100, step4:4.2},
    {name:"total",step1:120, step2:120, step3:120, step4:100}
    ];

    $: tweenedX = tweened(data.map((d) => d.step1),{
        duration: 800,
        easing: cubicOut
    });

    
    const step2 = function () {
        tweenedX.set(data.map((d) => d.step2));
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

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>
    <div class="container" style="width={width}; height:{height}">
        <svg {width} height={height}>
            {#each data as circle, index}
            <circle 
                cx={width/2} 
                cy={height/2}
                r={xScale($tweenedX[index])} 
                fill="none" 
                stroke={ $tweenedX[index] >= 100 ? "green" : "black"}
                stroke-width={ $tweenedX[index] > 118 ? "0px" : "3px"}
                transition:fade={{duration : 600}}/>
            {/each}     
        </svg>
    </div>


<style>
    .container {
        background: whitesmoke;
        box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
        top: 10%;
        margin: 0 auto;
        overflow: hidden;
    }
</style>