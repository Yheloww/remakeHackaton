<script>

import { fly } from "svelte/transition";
let percentage = 50;
$: response = "";
$: answer= "";


function handleClick() {
		if(percentage == 4){
			response = "Bien joué ! Dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à";
		} else if ( percentage < 10 ){
			response= 'Pas si loin ! En réalité, dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à ';
		} else if (percentage >= 10){
			response = 'Oups, raté… En réalité, dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à ';
		}
		answer = "on vous explique pourquoi c'est problématique ...";
	}


</script>




<section id="question-1" class="section">
    <div id="Q1-right-section" class="half-section">
            {#if answer}
            <h1 class="big"  transition:fly="{{ x: -500, duration: 2000 }}">3.9%</h1>
            <p transition:fly="{{ x: -500, duration: 2000 }}"> {response} </p>
            <p transition:fly="{{ x: -500, duration: 2000 }}"> <b>{answer}</b> </p>
            {/if}
      
    </div>
    <div id="Q1-left-section" class="half-section">
        <h1 style="margin-right:25%;">
            Quel pourcentage de cours dans les universités et hautes écoles belges traite des enjeux climatiques?
        </h1>
        <div class="input-section">
            <div class="slider">
                <p>{percentage}</p>
                <input type="range" min="1" max="100" bind:value={percentage} class="slider tiny" id="courseRange">    
            </div>
         
            <button on:click={handleClick} class="tiny">confirmer</button>
        </div>
       
    </div>
</section>

<style>

    /* div {
        border: 2px solid red;
    } */
    #Q1-left-section{
        display: flex;
        margin-left: 50%;
        flex-direction: column;
        justify-content:space-around;

    }
    
    #Q1-right-section {
        position: absolute;
        margin-left: 15%;
        width: 25%;
    }
    .tiny {
        margin-top: 5%;
        margin-bottom: 5%;
    }

    .input-section{
        margin-top: 2%;
        display: flex;
        flex-direction: column;
        flex-basis: 50%;
        padding-right: 50%;
    }

   .slider {
    display: flex;
    margin-left: 1%;
   }
    </style>