<script>
    import { fade } from "svelte/transition";

    let src;
    let txt = "";
    let infos= "";
    
    function HE() {
        src = "/images/hauteecole-11.svg";
        txt = "Et non… Ce sont en fait les universités qui arrivent largement en tête. ";
        infos = "… contre 31% seulement par des hautes écoles ";
    }
    function unif() {
        src = "/images/université-10.svg"
        txt="Tout à fait ! Les universités arrivent largement en tête. "
        infos = "Si l’on s’intéresse à l’ensemble des cours qui traitent des enjeux climatiques en Belgique, on s’aperçoit que 69% sont dispensés par des universités… ";
    }

</script>



<section id="différence-HE-U">
    <div id="title">
        <h1 class="center">
            Là où une différence plus importante existe c'est entre les Hates école et universités. D'après-vous, La quelle de ces deux institutions possede l'offre la plus importante de cours traitant des enjeux climatique ?
        </h1>
    </div>
    <div id="bottom" class="section"> 
        <div id="left-bottom" class="half-section">
            <div class="section">
                <button class="HE-btn"on:click={HE}><span>Haute-ecole</span></button>
                <button on:click={unif} ><span>Universités</span></button>
            </div>
            <p> {txt} <br/> {infos}</p>
        </div>
        <div id="right-bottom" class="half-section">
            <img   transition:fade={{duration : 600}} {src} alt="" width="100%" id="graphique-HE-U" />
        </div>
    </div>
</section>

<style>
  
    .center {
        margin: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
        width: 75%;
        margin: 0 auto;
    }
    
    .section {
        display: flex;
        justify-content:space-evenly;
        flex-direction: row;
        align-items: top;
        width: 100%;

    }
    
    .half-section {
        flex-basis: 25%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    button {
        margin-top: 10%;
        font-size: medium;
        font-family: 'Avara-black';
        text-transform: uppercase;
        padding: 5px;
        background-color: white;
        border: 3px solid #048D14;
        color: #048D14;
        transform: skew(5deg);
        text-decoration: none;
    }

    button > span {
        display: inline-block;
        transform: skew(-5deg);
    }
    button:hover {
        background-color: #048D14;
        color: white;
    }

    .HE-btn {
        margin-right: 5%;
    }

    </style>