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

<style>
    section{
        border: 3px solid aquamarine;
        margin: 50px;
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
    </style>