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


<style>

    .center {
        margin: 20px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        align-items: center;
    }
    .section {
        display: flex;
        justify-content:space-evenly;
        flex-direction: row;
        align-items: top;
    }
    </style>