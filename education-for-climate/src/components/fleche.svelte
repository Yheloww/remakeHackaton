<script>
    import Scroll from "./Scrolly.svelte";
    import { fly } from "svelte/transition";
    let currentStep;
    let steps = [
        "",
        "",
        ""
    ]
    function custom(node, params) {
            return {
            css: (t,u) => `transform: rotate(${u * 0.5}deg); opacity: ${t * 30}%`
        }}
</script>




<section id="flech">
  <div class="chart">
    <div class="img-fleche center">
      <img  transition:custom= {{ duration : 600}} src="./images/fleche.svg" alt="fleche" width="25%" id="fleche-img" class="rotate"/>
      <img src="./images/demi-rond.svg" alt="fleche" width="40%" id="graphique-HE-U"/>
     </div>
      <div class="text">
          <p class="base">L’asbl The Shifters Belgium, qui promeut l’éducation sur le climat dans l’enseignement supérieur belge, a mené en 2022 une enquête auprès de 600 étudiants. 87% de ceux-ci pensent que « les universités belges doivent dispenser des modules d’enseignement sur le changement climatique ». </p>
          {#if currentStep >= 1}
          <h1 transition:fly="{{ x: -500, duration: 2000 }}" class="big base"> 87% </h1>
          {:else}
          <h1 class="big base transparent"> 87% </h1>
          {/if} 
      </div>
  </div>
    <div class="fleche-text center">
        <Scroll bind:value={currentStep}>
            {#each steps as text, i}
                <div class="step" class:active={currentStep === i}>
                    <div class="step-content">
                        <p>{text}</p>
                    </div>
                </div>
            {/each}
        </Scroll>
    </div>
  </section>

<style>

    .center {
        margin: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }

    .step {
      height: 90vh;
      display: flex;
      place-items: center;
      justify-content: center;
      margin-right: 45%;
      margin-left: 3%;
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
    justify-content: space-evenly;
    flex-direction: column;
  }

  .text {
    display: flex;
    flex-direction: row-reverse;
    justify-content: center;
    width: 100%;
    align-items: center;
    flex-basis: 75%;
  }

  .base {
    flex-basis: 25%;
  
  }

  h1 {
    margin-top: 0;
    margin-bottom: 0;
    justify-self: right;
  }
  p{
    margin-top: 0;
    margin-bottom: 0;
  }
  #fleche-img {
    margin-top:17%;
    margin-right: 25%;
  }

  .transparent {
    opacity: 0;
  }
  #graphique-HE-U{
    position: absolute;
  }

  @keyframes rotate {
    from {
      transform: rotate(0);
    }
    50% {
      transform: rotate(156.6deg)
    }
    to {
      transform: rotate(0deg);
    }
  }

  .rotate {
    animation: rotate 6s infinite both;

    transform-origin: center right;
  }

  @media (max-width: 600px) {
    .text {
      flex-direction: column;
    }
  }
    </style>