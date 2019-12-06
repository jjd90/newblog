---
layout: post
title: "Creating a webpage with a map using Google Maps API "
date: 2019-12-06
categories: Blog
background: '/img/posts/09.jpeg'
---

Hi Everyone, 

For this blog post I will be walking you through the process of working with Google Maps api and creating an html file that will display a map on a webpage.

1. First you will need to create an account with google maps platform. Click on the link below to navigate to that page.

     https://cloud.google.com/maps-platform/?_ga=2.21995963.1280624522.1575611520-2022702463.1575611520#get-started
     
     Make sure to only select the Maps option.
     Name the project whatever you would like.
       Note: you will need a credit card, you can use a prepaid card. For our purposes the cost will be very minimal and just cost a few cents. You do receive a $100 credit.

2. Next you will need to generate an API key, luckily you get prompted to create one once you have finished signing up. Copy the key into a text document as we will be using it for this tutorial

3. Now is the process of creating the HTML file. Go ahead an create a file with the .html extension. 

4. Next, we need to write in the code that will declare the file as an HTML document. The code is below:
<pre><code class="html">
   <!DOCTYPE html>
     <html lang="en">
       <head>
         <title>Matador Discounts</title>
         <meta charset="utf-8">
  	 <meta http-equiv="X-UA-Compatible" content="IE=edge">
	 <meta name="viewport" content="width=device-width, initial-scale=1">
 	</head>  
  	<body>
        </body>
    </html>
</pre>

5. Now, we will need to initialize the map also know as create the map. We will insert the code below into the body section of the html file. Goggle maps api is javascript code so we will need to also declare that the code is a script. I point out were we declare that in the code below:

   We will also be declaring a div in the html body which will be the exact location in which the map will appear. I will show that first

   <!DOCTYPE html>
     <html lang="en">
          <head>
    		    <title>Matador Discounts</title>
    		    <meta charset="utf-8">
  	       	<meta http-equiv="X-UA-Compatible" content="IE=edge">
		        <meta name="viewport" content="width=device-width, initial-scale=1">
 	        </head>  
  	         <body>
		           <div id="map"></div>         <----- at this line is where the map is generated
			         <script>
				                         <----- where the map code goes (code below)
			         </script>
             </body>
   </html>

   Now that we have declared a div that specifies the location at which we want the map to show up we can insert the code that actually initialized the map.

