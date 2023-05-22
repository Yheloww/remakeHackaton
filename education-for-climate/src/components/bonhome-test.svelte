<script>
  import {pathBonhomme} from "../components/path.js";
  import * as d3 from 'd3'
  import { onMount } from "svelte";

  let height;
  let width;

onMount(() => {

console.log(pathBonhomme);

	//number of icons to color in to visualize percent
	let percentNumber = 5;

	//variables for the font family, and some colors
	let fontFamily = "helvetica";
	let twitterFill = "black";
	let twitterFillActive = "#048D14";
	let svgBackgroundColor = '#00000';

	let width = 1000;
	let height = 1000;

	//create an svg with width and height
	let svg = d3.select('#grid-chart')
		.append('svg')
		.attr("width", width)
		.attr("height", height)
    	.style('background-color', svgBackgroundColor);

    // bonhomme path
    var bonhomme = svg.append("defs")
		.append("g")
		.attr("id","bonhomme")
		.append("path")
		.attr("d", pathBonhomme)
		.attr("transform", "scale(1.2)");
    

	//10 rows and 10 columns 
	let numRows = 8;
	let numCols = 13;

	//x and y axis scales
	let y = d3.scaleBand()
		.range([0,width])
		.domain(d3.range(numRows));

	let x = d3.scaleBand()
		.range([0, height])
		.domain(d3.range(numCols));

	//the data is just an array of numbers for each cell in the grid
	let data = d3.range(numCols*numRows);

	//container to hold the grid
	let container = svg.append("g")
	
        container.selectAll("use")
        .data(data)
        .enter().append("use")
        .attr("href" , "#bonhomme")
        .attr("id", (d) => "id"+d)
        .attr('x', (d) =>  x(d%numCols))
        .attr('y', (d) => y(Math.floor(d/numCols)))
        .attr('fill', (d) => d < percentNumber ? twitterFillActive : twitterFill )

})


</script>

<svelte:window bind:innerHeight={height} bind:innerWidth={width}/>

<div id='grid-container'>
    <div id='grid-chart'></div>
</div>

