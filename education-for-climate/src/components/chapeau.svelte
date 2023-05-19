<script>

    window.onscroll = function() {
            var theta = document.documentElement.scrollTop / 50 % Math.PI;

    document.getElementById('terre')
    .style.transform ="rotate(" + window.pageYOffset/4 + "deg)";
    }
</script>



<section id="Premier">
    <div class="center" id="entete">
        <img src="/images/hacktualite.svg" alt="hacktualité" width="10%"/>
    </div>
    <div class="not-center" id="chapeau">
        <img src="/images/titre_footer-02.svg" alt="changement scolaire pas climatique" width="75%"/>
    </div>
    <div class="texter">
        <p id="text-chapeau" class="txt-princi">Malgré l'urgence climatique à laquelle nous sommes confrontés, les universités et hautes écoles belges semblent ne pas accorder suffisamment d'importance à la formation sur le climat. En effet, peu de cours spécifiques sont proposés aux étudiants pour leur permettre de comprendre les enjeux environnementaux actuels et d’entrer dans une nouvelle génération de professionnels avertis. Dans cet article, nous vous amenons à constater le manque cruel de présence de cours sur le climat dans l’enseignement supérieur belge. </p>
    </div>
    <div class="center" id="terre">
        <img src="/images/planete.svg" alt="planète terre" width="30%"/>
    </div>
</section>

<style>
   
   :global(section){
        border: 2px solid aquamarine;
        margin-bottom: 10%;
   }
    .center {
        margin: 50px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }
    
    #chapeau {
        margin-left: 10%;
    }

    .texter {
        margin-left: 38%;
        margin-right: 15%;
    }



    </style>