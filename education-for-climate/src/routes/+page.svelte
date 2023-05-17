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
</script>

<Chapeau/>

<Question1/>

<Pacte/>

<Bonhomme/>

<Round/>

<DifferenceHe/>

<Fleche/>

<Solution/>

<div id="footer">
    <img src="/images/footer.svg" alt="différence ue unif" width="25%"/>
</div>
<style>

#footer {
    margin:0;
}
</style>