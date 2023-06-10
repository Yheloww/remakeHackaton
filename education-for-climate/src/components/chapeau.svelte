<script>

import { onMount } from "svelte";

// onMount(() => {
//     window.onscroll = function() {
//             var theta = document.documentElement.scrollTop / 50 % Math.PI;

//     document.getElementById('planete')
//     .style.transform ="rotate(" + window.pageYOffset/2 + "deg)";
//     }
// })
$: width = 1000;
$: height = 1000;
 
</script>

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>


<section id="Premier" width={width}>
    <div class="center" id="entete">
        <img src="./images/hacktualite.svg" alt="hacktualité" class="entete" width="40%"/>
    </div>
    <div class="center" id="chapeau">
        {#if width > 600}
        <img src="./images/titre_footer-02.svg" alt="changement scolaire pas climatique" class="titre"/>
        {:else}
        <img src="./images/titre-07.svg" alt="changement scolaire pas climatique" class="titre"/>
        {/if}
    </div>
    <div class="texte">
        <p id="text-chapeau" class="txt-princi">Malgré l'urgence climatique à laquelle nous sommes confrontés, les universités et hautes écoles belges semblent ne pas accorder suffisamment d'importance à la formation sur le climat. En effet, peu de cours spécifiques sont proposés aux étudiants pour leur permettre de comprendre les enjeux environnementaux actuels et d’entrer dans une nouvelle génération de professionnels avertis. Dans cet article, nous vous amenons à constater le manque cruel de présence de cours sur le climat dans l’enseignement supérieur belge. </p>
    </div>
</section>

<div id="terre">
    <img src="./images/planete.svg" alt="planète terre"  id="planete" class="planete" width="100%"/>
</div>

<style>
    /* :global(div) {
        border : 2px solid red
    }
    :global(section) {
        border: 2px solid aquamarine;
    } */
    #entete {
        display: flex;
        justify-content: center;
        margin-block: 0.75rem;
    }
    section {
        margin-inline: 1rem;
    }
    
    .texte {
        position: relative;
    }

    p{
        font-size: 0.85rem;
        font-family: "LunchType_Medium_Expanded";
    }

    :global(img) {
        border: 2px solid green;
    }

    </style>