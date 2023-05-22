<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut, elasticOut } from 'svelte/easing';
    import {fade, fly} from 'svelte/transition';
    import { each } from 'svelte/internal';

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
<section  style="width={width}; height:{height}" class="test">
    <h1 class="center">Dans quelle région les universités et hautes écoles proposent-elles la plus grande poportion de cours traitant des enjeux climatiques ?</h1>
    <div class="bnt-region section">
        <button class="btn-1" on:click={step1}><span>Bruxelles</span></button>
        <button class="btn-2" on:click={step2}><span>Wallonie</span></button>
        <button class="btn-3" on:click={step3}><span>Flandre</span></button>
        <button class="btn-4" on:click={step4}><span>total</span></button>
    </div>
    <div class="raltive-p">
        {#if WalSticker}
        <img class="wallonie" width="10%" src="./images/wallonie-08.svg" alt ="wallonie"transition:custom= {{}}/>
        {/if}
        {#if FlaSticker}
    >   <img class="flandre" width="10%" src="./images/flandre-09.svg" alt ="wallonie"transition:custom= {{}}/>
        {/if}
        {#if totalText}
        <p class="total" transition:custom= {{}}>Ce cercle vert correspond à 100% des cours</p>
        {/if}
        {#if BxlSticker}
        <img class="bruxelles" width="10%" src="./images/bruxelles-07.svg" alt ="wallonie"transition:custom= {{}}/>
        {/if}
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
            {/each}
    </div>
</section>


<style>
    .raltive-p {
        position: relative;
    }
    
    .center {
        margin: 10px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
        width: 75%;
        margin: 0 auto;
    }
    .section {
        display: flex;
        justify-content:center;
        flex-direction: row;
        align-items: top;
    }
    button {
        margin-left: 30px;
        margin-right: 30px;
        margin-top: 1%;
        font-size: medium;
        font-family: 'Avara-black';
        text-transform: uppercase;
        padding: 5px;
        background-color: white;
        border: 3px solid #048D14;
        color: #048D14;
        transform: skew(5deg);
        text-decoration: none;
    }
    
    button > span {
        display: inline-block;
        transform: skew(-5deg);
    }
    button:hover {
        background-color: #048D14;
        color: white;
    }

    .bruxelles {
        position: absolute;
        top: 20vh;
        left: 60vw;
    }
    
    .wallonie {
        position: absolute;
        top: 30vh;
        left: 32vw;
    }
    .flandre {
        position: absolute;
        top: 32vh;
        left: 60vw;
    }

    .total {
        position: absolute;
        top: 50vh;
        left: 40.5vw;
        text-align: center;
        width: 20%;
      
    }
    </style>