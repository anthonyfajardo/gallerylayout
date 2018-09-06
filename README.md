# gallerylayout
A simple gallery layout using pure html and css with css grid

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	
	<title>Snippets</title>
</head>

<style>

	/*container that holds the whole gallery*/
	.container{
		max-width: 1200px;
		margin: 0 auto;
	}

	/*Check to see if display: grid works*/
	@supports(grid-area: auto){
		.wrapper{
			max-width: 768px;
			margin: 0 auto;
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: repeat(3, 1fr);
			grid-gap: 10px;
			margin: 10px auto;
		}
	}
	
	/*set a minimum widht and height for the div with a class of box to see the images. 
	Without the minimum width and height, you will not see any images*/
	.box{
		min-width: 100px;
		min-height: 200px;
		border: 1px solid black;
		position: relative;
		z-index: 1;
		overflow: hidden;
	}

	/*the pseudo element before will hold the orange border.  Positioning the div like this will ensure
	that the pseudo element before will cover the entire div*/
	.box:before{
		content: "";
		position: absolute;
		top: 10px;
		bottom: 10px;
		left: 10px;
		right: 10px;
		border: 2px solid orange;
		z-index: -1;		
	}

	/*the pseudo element after will hold the image for the div and the images will be set as the background*/
	.box:after{
		content: "";
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;		
		background-size: cover!important;
		background-position: center!important;
		background-repeat: no-repeat!important;
		z-index: -10;
		transition: 0.3s ease-in-out; /*transition speed of the hover effect*/
	}

	/*This is the hover effect for the pseudo element after for each boxes*/
	.box:hover:after{
		transform: scale(1.2);
	}


	/*This provides the images on the pseudo elemnt after.*/
	.box:nth-child(4n+1):after{	background: url('https://unsplash.it/300/300/?random');	}
	.box:nth-child(4n+2):after{	background: url('https://unsplash.it/400/400/?random');	}
	.box:nth-child(4n+3):after{	background: url('https://unsplash.it/500/500/?random');	}
	.box:nth-child(4n+4):after{	background: url('https://unsplash.it/600/600/?random');	}



	/*this determines the grid positions of the div with a class of box*/
	.box:nth-child(4n+1){
		grid-column: 1/3;
		grid-row: 1/3;
	}
	.box:nth-child(4n+2){
		grid-column: 3/4;
		grid-row: 1/2;		
	}
	.box:nth-child(4n+3){
		grid-column: 3/4;
		grid-row: 2/3;		
	}
	.box:nth-child(4n+4){
		grid-column: 1/4;
		grid-row: 3/4;		
	}

	/*this nth-child(even) will change the grid positions of ONLY the even boxes*/
	.wrapper:nth-child(even) .box:nth-child(4n+1){
		grid-column: 1;
		grid-row: 1/2;
	}
	.wrapper:nth-child(even) .box:nth-child(4n+2){
		grid-column: 1;
		grid-row: 2/3;		
	}
	.wrapper:nth-child(even) .box:nth-child(4n+3){
		grid-column: 2/4;
		grid-row: 1/3;		
	}	


</style>

<body>

	<div class="container">

		<div class="wrapper">
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
		</div>
		<div class="wrapper">
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
		</div>
		<div class="wrapper">
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
		</div>
		<div class="wrapper">
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
			<a href="#" class="box"></a>
		</div>
	</div>
	
</body>
</html>
