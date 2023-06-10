<script>
import Scroll from "./Scrolly.svelte";
import { fade, fly } from "svelte/transition";
import {pathBonhomme} from "../components/path.js";
import * as d3 from 'd3'
import { onMount } from "svelte";
import { each } from "svelte/internal";
import { tweened } from "svelte/motion";

$: height = 1000;
$: width = 1000;
let currentStep;
let step;
$: year = 2022;



let fontFamily = "helvetica";
let bonhommeFill = "black";
let bonhommeFillActive = "#048D14";
let svgBackgroundColor = '#00000';

let numRows = 10;
let numCols = 10;

let data = d3.range(numCols*numRows);
data.splice(data.length)
console.log(data.length)
//x and y axis scales
$: y = d3.scaleBand()
		.range([0, 500])
		.domain(d3.range(numRows));

$: x = d3.scaleBand()
		.range([370,0])
		.domain(d3.range(numCols));
      
let steps = [
    "Au sein de la population active de notre pays, seulement 1 personne sur 20 a reçu un enseignement qui aborde les questions climatiques. ",
    "En supposant une transformation rapide de la majorité des formations d’ici dix ans, il faudrait attendre 2045 pour passer à 1 personne sur 3. ",
    "Ce n’est qu’en 2060 que l’on pourrait espérer voir la moitié de la population active belge formée aux questions climatiques. C’est un changement qui est donc possible, mais qui demande du travail.",
    "Les universités et les hautes écoles, qui forment près de la moitié de la population en Belgique, doivent par conséquent améliorer leur offre de cours qui abordent les enjeux climatiques si elles souhaitent être en accord avec le Pacte vert européen. ",
    "Le manque de données disponibles ne permet malheureusement pas d’analyser l’évolution de cette offre au fil du temps. Nous pouvons cependant analyser la situation actuelle. "
]

$: percent = 5;

    $: step1 = tweened(data.map((d) => d.step1))

    const step2 = function () {
        tweenedX.set(data.map((d) => d.step2));
    };

    const step3= function () {
        tweenedX.set(data.map((d) => d.step3));
    };


    $: {
    if (currentStep == 0) {
        percent=5;
        year="Aujourd'hui";
    }
    if (currentStep == 1) {
        percent=33;
        year="2045";
    }
    if (currentStep >= 2) {
        percent=50;
        year="2060";
    }
  }

</script>


<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>
<section class="section">
    <div id="perso-left" class="chart">
            <h1 id="title-population">
                pourcentage de population active
            </h1>
                <div id='grid-chart'>
                    <svg width=360 height=500>
                        <def>
                            <g id="bonhomme">
                                <path d={pathBonhomme}
                                transform="translate(-10,-105) scale(0.58)">
                                </path>
                            </g>
                        </def>
                        <g>
                            {#each data as d, index}
                            <use href="#bonhomme"
                                 id="id = {d}"
                                 x={ x(d%numCols)}
                                 y={ y(Math.floor(d/numCols))}
                                 fill={d <= percent ? bonhommeFillActive : bonhommeFill}
                                 transition:fade={{duration:200}}
                                 step={currentStep}></use>
                            {/each}
                        </g>
                    </svg>
                    <h1 id="sticker" 
                        step={currentStep} 
                        transition:fade={{duration: 600}}>{year}</h1>
                </div>
            </div>
    <div>
        <Scroll bind:value={currentStep}>
            {#each steps as text, i}
                <div class="step" class:active={currentStep === i}>
                    <div class="step-content">
                        <p>{text}</p>
                    </div>
                </div>
            {/each}
        </Scroll>
</section>



<style>

section {
    margin-bottom: 3rem;
}

#sticker {
    font-size: "Avara-black";
    background-color: green;
    color: white;
    margin-inline: 6rem;
    padding: 0.25rem;
    font-size: 1.8rem;
    position: absolute;
    bottom: -3rem;
    left: -3.5rem;
    padding-top:0.7rem
}
h1 {
    text-align: center;
    margin-inline: 2rem;
    font-size: 1.2rem;

}

.step {
      height: 90vh;
      display: flex;
      place-items: center;
      justify-content: center;
    }
  
    .step-content {
      background: #F9F8F4;
      color: #ccc;
      padding: .5rem 1rem;
      transition: background 500ms ease, color 500ms ease;
      box-shadow: 1px 1px 10px rgba(0, 0, 0, .2);
      flex-basis: 75%;
      border-radius: 10px;
    }
  
      .step.active .step-content {
          background: white;
          color: black;
      }

      .chart {
    background: #F9F8F4;
    width: 100%;
    height: 100%;
    position: sticky;
    top: 10%;
    margin: auto;
    z-index: -100;
  }
</style>