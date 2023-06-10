<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut, elasticOut } from 'svelte/easing';
    import {fade, fly} from 'svelte/transition';
    import Chapeau from '../components/chapeau.svelte';
    import Question1 from '../components/Question1.svelte';
    import Pacte from '../components/pacte.svelte';
    import Bonhomme from '../components/bonhomme.svelte';
    import Round from '../components/round.svelte';
    import DifferenceHe from '../components/differenceHE.svelte';
    import Fleche from '../components/fleche.svelte';
    import Solution from '../components/solution.svelte';
    import BonhomeTest from '../components/bonhome-test.svelte';

    $: height = 1000;
    $: width = 1000;

</script>

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>
<head>Education for climate</head>
<div class="wrapper" width={width}>
    <Chapeau/>

    <Question1/>

    <Pacte/>

    <Bonhomme/>
            
    <Round/>
    
    <DifferenceHe/>

    <Fleche/>
        
    <Solution/>
</div>


<div id="footer">
    <img id="footer" src="./images/titre_footer-01.svg" alt="différence ue unif" width="100%"/>
</div>
<style>


#footer {
    margin:0 auto;
}

@media( max-width: 600px){
    :global(p) {
        font-size: 1rem;
    }
    :global(h1) {
        font-size: 1rem;
    }

}
</style>