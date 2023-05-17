<script>
    import * as d3 from 'd3'
    import Scrolly from "../components/Scrolly.svelte";
    import { tweened } from "svelte/motion";
    import { cubicOut, elasticOut } from 'svelte/easing';
    import {fade, fly} from 'svelte/transition';

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

<section id="question-1" class="section">
    <div id="Q1-Left-section" class="half-section">
        <h1 class="big">
            3.9%
        </h1>
        <h1> BOh </h1>
        <p> Boh 2 </p>
    </div>
    <div id="Q2-right-section" class="half-section">
        <h1>
            Quel pourcentage de cours ?
        </h1>

        <input type="range" min="1" max="100" value="50" class="slider" id="courseRange">

        <button>confirmer</button>
    </div>
</section>

<section id="pacte">
    <div class="backgound-img">
        <div id="pacte-img">
            <img src="/images/txt-document.svg" alt="pacte" width="250%" id="img-pacte"/>
        </div>
        <div id="pacte-txt">
            <h1>
                Commission européenne : 
                Le pacte vert pour l'Europe
            </h1>
            <div>
                <p>
                    Scrolly text
                </p>
            </div> 
        </div>
    </div>
</section>

<section class="section">
    <div id="perso-left" class="half-section">
        <h1>
            pourcentage de population active
        </h1>
        <p>
            changing text
        </p>
    </div>
    <!-- Animation with persos -->
    <div id="perso-right" class="half-section">
        <img src="/images/bonhomme_tous-12.svg" alt="pacte" width="100%" />

    </div>
</section>

<section id="round">
    <h1 class="center">Dans quelle région les universités et hautes écoles proposent-elles la plus grande poportion de cours traitant des enjeux climatiques ?</h1>
    <div class="bnt-region section">
        <button id="bruxelles">Bruxelles</button>
        <button id="flandres">Flandre</button>
        <button id="wallonie">Wallonie</button>
    </div>
    <div id="rond-graphique">
        <svg width="500" height="500">
            <circle cx=250 cy=250 r=25/>
        </svg>
    </div>
</section>

<section id="différence-HE-U">
    <div id="title">
        <h1 class="center">
            Là où une différence plus importante existe c'est entre les Hates école et universités. D'après-vous, La quelle de ces deux institutions possede l'offre la plus importante de cours traitant des enjeux climatique ?
        </h1>
    </div>
    <div id="bottom" class="section"> 
        <div id="left-bottom" class="half-section">
            <div class="section">
                <button>Haute-ecole</button>
                <button>Universités</button>
            </div>
            <p> Texte qui change </p>
        </div>
        <div id="right-bottom" class="half-section">
            <img src="/images/université-10.svg" alt="différence ue unif" width="100%" id="graphique-HE-U"/>
        </div>
    </div>
</section>

<section id="flech">
    <div class="img-fleche center">
        <img src="/images/fleche2-14.svg" alt="différence ue unif" width="25%" id="graphique-HE-U"/>
    </div>
    <div class="fleche-text center">
        <h1 class="big"> 87% </h1>
        <p>Textttttt</p>
    </div>
</section>

<section id="solutions">
        <div id="header-solution" class="center">
            <h1>Alors que faire pour pallier ce manque et répondre à la demande des étudiants ?</h1>
            <p>Textttttt</p>
        </div>
        <div id="bottom-solution" class="section">
            <div id="left-solution" class="third-section">
                <img src="/images/solution1-15.svg" alt="différence ue unif" width="100%" id="graphique-HE-U"/>
                <p>Textttt</p>
            </div>
            <div id="center-solution" class="third-section">
                <img src="/images/solution2-16.svg" alt="différence ue unif" width="100%" id="graphique-HE-U"/>
                <p>Textttt</p>
            </div>
            <div id="right-solution" class="third-section">
                <img src="/images/solution3-17.svg" alt="différence ue unif" width="100%" id="graphique-HE-U"/>
                <p>Textttt</p>
            </div>
        </div>
        <div class="final-text center">
            <p> Texxxxtttt</p>
        </div>
    </section>
<div id="footer">
    <img src="/images/footer.svg" alt="différence ue unif" width="25%"/>
</div>
<style>
section{
    border: 3px solid aquamarine;
    margin: 50px;
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

div {
    border: 5px solid red;
}

.section {
    display: flex;
    justify-content:space-evenly;
    flex-direction: row;
    align-items: top;
}

.half-section {
    flex-basis: 25%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.third-section {
    flex-basis: 30%;
    display: flex;
    flex-direction: column;
}

#pacte-txt {
    margin-left: 35%;
    position: relative;
    z-index:100;
}

#pacte {
    position:relative;
    height: 1000px;
}

#pacte-img {
    display: block;
    position:absolute;
    z-index: -100;
    margin-top: 100;
}

#img-pacte {
    transform: rotate(-50deg);
    opacity: 0.5;
}

#footer {
    margin:0;
}
</style>