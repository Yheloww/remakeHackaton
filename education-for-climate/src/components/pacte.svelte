<script>
    import Scroll from "./Scrolly.svelte";
    import { fly } from "svelte/transition";
      
    let currentStep;
    const steps = ["En 2020, le Parlement européen a voté le Pacte vert pour l’Europe. Objectif : une Union européenne neutre en carbone d’ici 2050. ", 
                   "Le pacte insiste notamment sur l’importance de l’enseignement pour effectuer cette transition.", 
                   "En effet, si l’on souhaite comprendre les causes du changement climatique et mettre en place des solutions pour le combattre, il est nécessaire de développer des compétences nouvelles dans tous les domaines. Cela passe notamment par les hautes écoles et les universités.",
                   "Pourtant, en Belgique, on est loin de répondre à cet objectif…",
                  "/images/loi.svg"];
  </script>
  
  <section>

    <div class="chart">
        <div class="title">
            <h1 class="title-text">
                Commission européenne : <br/>
                Le pacte vert pour l'Europe
            </h1>
        </div>
        <img id="img-pacte" src="./images/pacte.svg" alt="pacte" width="75%"/>
    </div>
      <Scroll bind:value={currentStep}>
          {#each steps as text, i}
              <div class="step" class:active={currentStep === i}>
                  <div class="step-content">
                      {#if currentStep == 4}
                      <img transition:fly="{{ x: -500, duration: 2000 }}" src="{text}" alt="">
                      {:else}
                      <p>{text}</p>
                      {/if}
                  </div>
              </div>
          {/each}
      </Scroll>
  </section>
  
  <style>
      :global(body) {
          background: #F9F8F4;
      }
    /* div{
      border: 1px solid red;
    } */
      
    .step {
      height: 90vh;
      display: flex;
      place-items: center;
      justify-content: center;
      margin-left: 50%;
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
  #img-pacte {
        transform: rotate(-5deg) translate(0,-100px);
        opacity: 0.5;
}

    .title {
        display: flex;
        justify-content: center;
        margin-left: 40%;
        width: 40%;

    }
  </style>