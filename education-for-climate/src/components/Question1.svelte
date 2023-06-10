<script>

import { fly } from "svelte/transition";
let percentage = 50;
$: response = "";
$: answer= "";


function handleClick() {
		if(percentage == 4){
			response = "Bien joué ! Dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à 4%";
		} else if ( percentage < 10 ){
			response= 'Pas si loin ! En réalité, dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à 4%';
		} else if (percentage >= 10){
			response = 'Oups, raté… En réalité, dans l’enseignement supérieur belge, la proportion de cours qui abordent les enjeux climatiques est légèrement inférieure à 4%';
		}
		answer = "on vous explique pourquoi c'est problématique ...";
	}


</script>




<section id="question-1" class="section">
    <div id="Q1-left-section" class="half-section">
        <h1>
            Quel pourcentage de cours dans les universités et hautes écoles belges traite des enjeux climatiques?
        </h1>
        <div class="input-section">
            <div class="slider">
                <div id="text-div">
                    <p style="margin-right:2%;">{percentage} %</p>
                </div>
                <input type="range" min="1" max="100" bind:value={percentage} class="slider tiny" id="courseRange">    
            </div>
         
            <button on:click={handleClick} class="tiny"><span>confirmer</span></button>
            
        </div>

        <div id="Q1-right-section" class="half-section">
          {#if answer}
          <p transition:fly="{{ x: -500, duration: 2000 }}"> {response} </p>
          <h1  transition:fly="{{ x: -500, duration: 2000 }}" class="big">3.9%</h1>
          <p transition:fly="{{ x: -500, duration: 2000 }}"> <b>{answer}</b> </p>
          {/if}
    
  </div>
       
    </div>
</section>

<style>

    h1{
      text-align: center;
    }

    section {
      margin-inline: 1rem;
    }
    .input-section {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .big {
      font-size: 7rem;
    }




    button {
        margin-right: 30px;
        margin-top: 1%;
        font-size: medium;
        font-family: 'Avara-black';
        text-transform: uppercase;
        padding-top: 5px;
        padding-bottom: 5px;
        position: inline;
        background-color: white;
        border: 3px solid #048D14;
        color: #048D14;
        transform: skew(5deg);
        text-decoration: none;
        width: 50%;
        transition: all 0.5s;
    }

    button > span {
        display: inline-block;
        transform: skew(-5deg);
    }
    button:hover {
        transform: translate(0,-5px);
        background-color: #048D14;
        color: white;
        text-decoration: none;
    }
    button:focus {
      transform:translate(0,5px);
      text-decoration: none;
    }


    input[type=range]:focus {
  outline: none;
  }
  
  input[type=range]::-webkit-slider-runnable-track {
  width: 100%;
  height: 26px;
  cursor: pointer;
  background: #FFFFFF;
  border-radius: 24px;
  border: 4px solid #000000;
}
input[type=range]::-webkit-slider-thumb {
  border: 1px solid #000000;
  height: 25px;
  width: 25px;
  border-radius: 12px;
  background: #000000;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: 1.5px;
}
input[type=range]:focus::-webkit-slider-runnable-track {
  background: #FFFFFF;
}
input[type=range]::-moz-range-track {
  width: 100%;
  height: 29px;
  cursor: pointer;
  background: #ffffff;
  border-radius: 24px;
  border: 4px solid #000000;
}
    input[type=range]::-moz-range-thumb {
  box-shadow: 0px 0px 1px #000000;
  border: 1px solid #000000;
  height: 23px;
  width: 23px;
  border-radius: 12px;
  background: #000000;
  cursor: pointer;
}
input[type=range]::-ms-track {
  width: 100%;
  height: 29px;
  cursor: pointer;
  background: transparent;
  border-color: transparent;
  color: transparent;
}
input[type=range]::-ms-fill-lower {
  background: #FFFFFF;
  border: 2px solid #000000;
  border-radius: 48px;
}
input[type=range]::-ms-fill-upper {
  background: #FFFFFF;
  border: 2px solid #000000;
  border-radius: 48px;
}
    input[type=range]::-ms-thumb {
  margin-top: 1px;
  box-shadow: 0px 0px 1px #000000;
  border: 1px solid #000000;
  height: 4vw;
  width: 4vw;
  border-radius: 12px;
  background: #000000;
  cursor: pointer;
}
input[type=range]:focus::-ms-fill-lower {
  background: #FFFFFF;
}
  

    </style>