<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut, elasticOut } from 'svelte/easing';
    import {fade, fly} from 'svelte/transition';

    let width = 1000;
    let height = 1000;

    let BxlSticker = true;
    let WalSticker = false;
    let FlaSticker = false;
    let totalText = false;

    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width/5]);

    let data = [
    {name:"Bruxelles",step1:100, step2:97, step3:83, step4:3.5},
    {name:"wallonie",step1:120, step2:100, step3:85.7, step4:3.6},
    {name:"Flandre",step1:120, step2:120, step3:100, step4:4.2},
    {name:"total",step1:120, step2:120, step3:120, step4:100}
    ];

    const tweenedX = tweened(data.map((d) => d.step1),{
        duration: 800,
        easing: cubicOut
    });

    const step2 = function () {
        tweenedX.set(data.map((d) => d.step2));
        WalSticker = true;
        BxlSticker = false;
        FlaSticker = false;
        totalText = false;
    };

    const step3 = function () {
        tweenedX.set(data.map((d) => d.step3))
        WalSticker = false;
        BxlSticker = false;
        FlaSticker = true;
        totalText = false;
    };

    const step4 = function () {
        tweenedX.set(data.map((d) => d.step4))
        WalSticker = false;
        BxlSticker = false;
        FlaSticker = false;
        totalText = true;
    };

    const step1 = function () {
        tweenedX.set(data.map((d) => d.step1))
        WalSticker = false;
        BxlSticker = true;
        FlaSticker = false;
        totalText = false;
    };

    function custom(node, params) {
        if (WalSticker) {
            return {
            css: (t,u) => `transform: translatex(${u * -200}px); opacity: ${t * 30}%`
        }}
        if (FlaSticker) {
            return {
            css: (t,u) => `transform: translatex(${u * 200}px); opacity: ${t * 30}%`
        }}
        if (totalText) {
            return {
            css: (t,u) => `transform: translatey(${u * 200}px); opacity: ${t * 30}%`
        }}
        if (BxlSticker) {
            return {
            css: (t,u) => `transform: translatex(${u * 200}px); opacity: ${t * 30}%`
        }}
        
    }
</script>

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>
<section>
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
                {#if WalSticker}
                <rect class="sticker" 
                      x={width/4} 
                      y={(height/2) - 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{}}/>
                {/if}
                {#if FlaSticker}
                <rect class="sticker" 
                      x={(width/4) + (width/5) * 2 } 
                      y={(height/2) - 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
                {#if totalText}
                <rect class="sticker" 
                      x={(width/2) - 50} 
                      y={((height/4)*3) - 50} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
                {#if BxlSticker}
                <rect class="sticker" 
                      x={(width/4)*3 - (width/100)*15} 
                      y={(height/4) + 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
            {/each}
            
        </svg>
        
        <div class="button">
            <button class="btn-1" on:click={step1}>Step 1</button>
            <button class="btn-2" on:click={step2}>Step 2</button>
            <button class="btn-3" on:click={step3}>Step 3</button>
            <button class="btn-4" on:click={step4}>Step 4</button>
        
        </div>
    </div>

</section>


<style>
    .container {
        background: whitesmoke;
        box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
        top: 10%;
        margin: 0 auto;
        overflow: hidden;
    }	

    .sticker {
        border-radius: 5px;
    }
</style>