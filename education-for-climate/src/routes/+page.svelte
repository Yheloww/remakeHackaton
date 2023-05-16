<script>
    import data from "../data/data";
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";

    let width = 1000;
    let height = 500;

    $: xScale = d3.scaleLinear()
    .domain([0,100])
    .range([0,width/5]);

    let currentStep;
    const steps = ["<p>Step 0!</p>", 
				   "<p>Step 1?</p>", 
				   "<p>Step 2.</p>",
                    ""];

</script>

<section>
    <div class="container" bind:clientWidth={width}>
        <svg {height} {width}>
            {#each data as circle}
            <circle 
            cx={width/2} 
            cy=250 r={xScale(circle.pourcentage)} 
            fill="none" 
            stroke={ circle.pourcentage == 100 ? "green" : "black"}
            stroke-width="2px"/>
            {/each}
        </svg>
    </div>
	<Scrolly bind:value={currentStep}>
		{#each steps as text, i}
			<div class="step" class:active={currentStep === i}>
				<div class="step-content">
					{@html text}
				</div>
			</div>
		{/each}
	</Scrolly>
</section>


<style>
    .container {
        background: whitesmoke;
        box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
        position: sticky;
        top: 10%;
        margin: 0 auto;
    }
    
  /* Scrollytelling CSS */
  .step {
    height: 80vh;
    display: flex;
    place-items: center;
    justify-content: center;
  }

  .step-content {
    background: whitesmoke;
    color: #ccc;
    border-radius: 5px;
    padding: 0.5rem 1rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    transition: background 500ms ease;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
    z-index: 10;
  }

  .step.active .step-content {
    background: white;
    color: black;
  }
	
</style>