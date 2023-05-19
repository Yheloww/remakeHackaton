<script>
import Scroll from "./Scrolly.svelte";
import { fly } from "svelte/transition";
      
let currentStep;
let steps = [
    "Au sein de la population active de notre pays, seulement 1 personne sur 20 a reçu un enseignement qui aborde les questions climatiques. ",
    "En supposant une transformation rapide de la majorité des formations d’ici dix ans, il faudrait attendre 2045 pour passer à 1 personne sur 3. ",
    "Ce n’est qu’en 2060 que l’on pourrait espérer voir la moitié de la population active belge formée aux questions climatiques. C’est un changement qui est donc possible, mais qui demande du travail.",
    "Les universités et les hautes écoles, qui forment près de la moitié de la population en Belgique, doivent par conséquent améliorer leur offre de cours qui abordent les enjeux climatiques si elles souhaitent être en accord avec le Pacte vert européen. ",
    "Le manque de données disponibles ne permet malheureusement pas d’analyser l’évolution de cette offre au fil du temps. Nous pouvons cependant analyser la situation actuelle. "
]
</script>



<section class="section">
    <div id="perso-left" class="chart">
            <h1>
                pourcentage de population active
            </h1>
            <img src="/images/bonhomme_tous-12.svg" alt="pacte" width="27%" />
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
    
    div {
        border: 2px solid red;
    }
    .section {
        display: flex;
        justify-content:space-evenly;
        flex-direction: column;
        align-items: top;
    }

    .step {
      height: 90vh;
      display: flex;
      place-items: center;
      justify-content: center;
      margin-right: 45%;
      margin-left: 3%;
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
    display: flex;
    flex-direction: row;
    justify-content: space-around;
  }
    </style>