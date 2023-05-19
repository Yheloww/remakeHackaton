<script>

    // window.onscroll = function() {
    //         var theta = document.documentElement.scrollTop / 50 % Math.PI;

    // document.getElementById('terre')
    // .style.transform ="rotate(" + window.pageYOffset/4 + "deg)";
    // }
</script>



<section id="Premier">
    <div class="center" id="entete">
        <img src="/images/hacktualite.svg" alt="hacktualité" width="25%"/>
    </div>
    <div class="not-center" id="chapeau">
        <img src="/images/titre-07.svg" alt="changement scolaire pas climatique" width="50%"/>
    </div>
    <div class="center">
        <p id="text-chapeau" class="txt-princi">texte du chapeau</p>
    </div>
    <div class="center" id="terre">
        <img src="/images/planete.svg" alt="planète terre" width="25%"/>
    </div>
</section>

<style>
   
   :global(section){
        border: 2px solid aquamarine;
        margin-bottom: 10%;
   }
    .center {
        margin: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }
    
    #chapeau {
        margin-left: 25%;
    }

    </style>