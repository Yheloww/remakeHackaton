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
$          {/if} 
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
    </style>