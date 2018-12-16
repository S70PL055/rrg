<!DOCTYPE html>
<html>

<head>
	<meta charset=utf-8 />
	<!-- Solid work! 😎 -->
	<!-- The title tag is what search engines and browsers use for your page title. -->
	<title>Red River Gorge Arches</title>

	<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.css" />
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.3.4/leaflet.css" />
	<link href="https://fonts.googleapis.com/css?family=Signika+Negative:300,700" rel="stylesheet">

	<!-- Add missing font -->
	<link href="https://fonts.googleapis.com/css?family=Dancing+Script" rel="stylesheet">


	<!-- Define the styles for our page elements -->
	<style>
		body {
			margin: 0;
			padding: 0;
			background: #f5f5f5;
			font-family: 'Signika Negative', sans-serif;
			color: #979797;
			font-size: 1.0em;
			font-weight: 300;
			line-height: 1.05em;
		}

		section {
			/* width: 890px; comment this out */
			width: 80%; /* change the width to a relative value. */
			margin: 20px auto;
		}

		h1 {
			font-size: 4em;
			font-family: 'Dancing Script', cursive;
			color: #333333;
		}

		h2 {
			font-size: 2em;
			font-family: 'Signika Negative', sans-serif;
			letter-spacing: .05em;
			font-weight: 300;
			color: #555555;
			padding: 20px 0 0 0;
		}

		h3 {
			font-size: 1.5em;
			font-family: 'Dancing Script', cursive;
			letter-spacing: .04em;
			color: #888888;
		}


		p {
			font-size: 1.1em;
			line-height: 1.4em;
		}

		a {
			color: #ff4323;
			text-decoration: none;
		}

		a:hover {
			text-decoration: underline;
			color: black;
		}

		ul {
			padding-left: 20px;
		}

		li {
			margin: 10px 0
		}

		#map {
			width: 100%;
			margin: 10px auto;
		}

		.max-image-width {
			width: 100%;
		}

		.linkbox {
			margin: 3px 0 20px 0;
			display: block;
			font-weight: 300;
		}

		hr {
			border: 0px;
			border-bottom: 1px solid #bbbbbb;
			padding-top: 20px;
		}

		#map {
			width: 100%;
			height: 540px;
			margin: 10px auto;
			border: 2px solid #d3d3d3;
		}
	</style>
</head>

<body>
	<section>
		<!--The title shown on the page-->
		<h1>Red River Gorge, KY </h1>

		<!-- The map -->
		<div id='map'></div>

		<!-- Your second heading -->
		<h2>WELCOME</h2>

		<p>
			To the Red River Gorge! Its a beautiful 29,000 acre area located within the Daniel Boone National Forest in eastern-central Kentucky. It contains numerous arches and is filled with steep valleys. Which makes it a popular place for climbers.
		</p>

		<p>
			While your there, take time to hike to the <a href="stargaparch/">Star Gap Arch.</a> It's one of the largest arches within the Red River Gorge, with a span of 72ft and a height of 83ft. Just be careful though as its surrounded on both sides by steep clifs!
		</p>

		<!-- Metadata about the project -->
		<p>This project was created as a part of the GEO 409 coursework in the Department of Geography at the University of Kentucky. The course used <a href="Lab-04.ipynb/">ArcGIS Pro and Python</a> scripting to process and analyze spatial data.</p>

		<h3>Geospatial PDF of Arches</h3>
		<img src="basemap\rrg.jpg" alt="basemap" width="100%">
		<a href="basemap\rrg.pdf">Download and use this map on your mobile device</a>
		<!-- Add you information below -->

		<h3>A Senic Location in the Gorge</h3>
		<img src="https://uky-gis.github.io/maps/us-arches/photos/don_juan_garden.jpg" alt="Don Juan Garden" width="100%">
		 <div class="linkbox">Don Juan's Garden photograph by UK Geography</div>

		 <h3>Interactive Map of US Arches</h3>
		 <a href="https://uky-gis.github.io/maps/us-arches/full">Map of US Named Arches (data from US GNIS)</a>


		<!-- More info about you -->
		<hr>
		<h3>More about Me!</h3>
		<ul>
			<li>See my projects on GitHub:
				<a href="https://github.com/S70PL055">S70PL055</a>, UKy GIS and Mapping</li>
		
			<!-- <li>Visit my
				<a href='#'>mapping portfolio</a>. </li> -->
		</ul>
	</section>

	<!-- Load the library that provides interactive map functionality -->
	<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.3.4/leaflet.js"></script>

	<!-- Make the instructions that tell the library how to handle requests -->
	<script>
		// FYI: The double forward slash makes a comment in the script tag

		// Define a variable that centers the intial view and zoom level. 
		var options = {
			center: [37.8332, -83.6077], // lat, long values of Gladie Visitor center
			zoom: 12.4 // Integer value. Higher value greater the scale.
		}

		// write a custom message for the Leaflet tooltip
		var message = 'The Red River Gorge';

		// ------------------------------------------------------ 
		// Below are parameters you can learn to manipulate in GEO 405 and GEO 672.
		
		// Create a Leaflet map in our division container with id of 'map'
		var map = L.map('map', options);

		// request some basemap tiles and add to the map
		var tiles = L.tileLayer('https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}{r}.png', {
			attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a> &copy; <a href="http://cartodb.com/attributions">Carto</a>',
			subdomains: 'abcd',
			maxZoom: 19
		}).addTo(map);

		// add a marker to the center of the map and open the tooltip
		L.marker(map.getCenter())
			.bindTooltip(message)
			.addTo(map)
			.openTooltip();
	</script>

</body>

</html>