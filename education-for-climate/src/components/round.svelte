<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut, elasticOut } from 'svelte/easing';
    import {fade, fly} from 'svelte/transition';

    let width = 1000;
    let height = 1000;

    let plotW = (width/100)*60;
    let plotH = (height/100)*60;

    let BxlSticker = true;
    let WalSticker = false;
    let FlaSticker = false;
    let totalText = false;

    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,plotW/2.5]);

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
<section  style="width={width}; height:{height}">
    <h1 class="center">Dans quelle région les universités et hautes écoles proposent-elles la plus grande poportion de cours traitant des enjeux climatiques ?</h1>
    <div class="bnt-region section">
        <button class="btn-1" on:click={step1}>bruxelles</button>
        <button class="btn-2" on:click={step2}>Wallonie</button>
        <button class="btn-3" on:click={step3}>Flandre</button>
        <button class="btn-4" on:click={step4}>Total</button>
    </div>
    <div class="container">
        <svg width={width} height={plotH}>
            {#each data as circle, index}
            <circle 
                cx={width/2} 
                cy={plotH/2}
                r={xScale($tweenedX[index])} 
                fill="none" 
                stroke={ $tweenedX[index] >= 100 ? "green" : "black"}
                stroke-width={ $tweenedX[index] > 118 ? "0px" : "3px"}
                transition:fade={{duration : 600}}/>
                {#if WalSticker}
                <rect class="sticker" 
                      x={width/4} 
                      y={(plotH/2) - 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{}}/>
                {/if}
                {#if FlaSticker}
                <rect class="sticker" 
                      x={(width/4) + (width/5) * 2 } 
                      y={(plotH/2) - 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
                {#if totalText}
                <rect class="sticker" 
                      x={(width/2) - 50} 
                      y={((plotH/4)*3) - 50} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
                {#if BxlSticker}
                <rect class="sticker" 
                      x={(width/4)*3 - (width/100)*15} 
                      y={(plotH/4) + 25} 
                      width="100" 
                      height="50" 
                      fill="green"
                      transition:custom= {{ duration : 600}}/>
                {/if}
            {/each}
            
        </svg>
    </div>
</section>




<!-- Html base
<section id="round">
    <h1 class="center">Dans quelle région les universités et hautes écoles proposent-elles la plus grande poportion de cours traitant des enjeux climatiques ?</h1>
    <div class="bnt-region section">
        <button id="bruxelles">Bruxelles</button>
        <button id="flandres">Flandre</button>
        <button id="wallonie">Wallonie</button>
    </div>
    <div id="rond-graphique">
        <svg width="500" height="500">
            <circle cx=250 cy=250 r=25/>
        </svg>
    </div>
</section> -->


<style>

    .center {
        margin: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }
    .section {
        display: flex;
        justify-content:space-evenly;
        flex-direction: row;
        align-items: top;
    }
    </style>