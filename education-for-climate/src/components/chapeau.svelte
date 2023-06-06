<script>

import { onMount } from "svelte";

onMount(() => {
    window.onscroll = function() {
            var theta = document.documentElement.scrollTop / 50 % Math.PI;

    document.getElementById('planete')
    .style.transform ="rotate(" + window.pageYOffset/2 + "deg)";
    }
})
$: width = 1000;
$: height = 1000;
 
</script>

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>


<section id="Premier" width="{width}">
    <div class="center" id="entete">
        <img src="./images/hacktualite.svg" alt="hacktualité" class="entete"/>
    </div>
    <div class="center" id="chapeau">
        {#if width > 600}
        <img src="./images/titre_footer-02.svg" alt="changement scolaire pas climatique" class="titre"/>
        {:else}
        <img src="./images/titre-07.svg" alt="changement scolaire pas climatique" class="titre"/>
        {/if}
    </div>
    <div class="texter">
        <p id="text-chapeau" class="txt-princi">Malgré l'urgence climatique à laquelle nous sommes confrontés, les universités et hautes écoles belges semblent ne pas accorder suffisamment d'importance à la formation sur le climat. En effet, peu de cours spécifiques sont proposés aux étudiants pour leur permettre de comprendre les enjeux environnementaux actuels et d’entrer dans une nouvelle génération de professionnels avertis. Dans cet article, nous vous amenons à constater le manque cruel de présence de cours sur le climat dans l’enseignement supérieur belge. </p>
    </div>
    <div id="terre">
        <img src="./images/planete.svg" alt="planète terre"  id="planete" class="planete"/>
    </div>
</section>

<style>
    #Premier {
        display: flex;
        flex-direction: column;
        justify-content: center;
        position: relative;
    }
    .center {
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }

    .texter {
        margin-left: 38%;
    }

    section {
        margin-bottom: 0%;
    }

    #terre {
        position: absolute;
        width:50%;  
        top: 30rem;     
    }
 
    .entete{
        width: 25%;
    }

    @media(max-width:600px) {
        .texter {
            margin-left: 2rem;
            margin-right: 2rem;
            margin-block: 2rem;
        }
        .planete {
           width:150%;
           margin: 0 auto;
        } 
        #terre {
            width: 150%;
            display: flex;
            justify-content: center;
            align-items: center;
            top: 25rem;
            left: -5rem;
        }

        #entete {
            margin: 2rem;
        }
        .entete {
            width: 25%;

        }
        .titre {
            margin-inline: 2rem;
        }

    }


    </style>