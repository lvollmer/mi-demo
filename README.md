# mi-demo
This repo contains the files associated with the Movable Ink coding challenge.

Original Instructions:
* This assignment is a javascript integration with the Weather Underground API.  

* The deliverable is an HTML file (or, if you want to split out js / css feel free to use multiple files).

* The HTML file should be reactive to the query string at the end of the URL.  So, for example, if the file is: index.html
it should be reactive to: index.html?zip_code=10011&date=08/30/2014

* The "zip_code" and "date" parameters will need to be used in the API request.  You can assume the merged in "date" will be within the next ten days.  This endpoint should give you what you need:
http://www.wunderground.com/weather/api/d/docs?d=data/forecast10day

* Use that data to create a page with the attached creative spec.  Use Helvetica for all fonts instead of what is in the image. The icons used in this crop are available here: http://www.wunderground.com/weather/api/d/docs?d=resources/icon-sets

* If the page must error out, it should appear as a blank page (should either be completely functioning or completely blank).

* Lastly, when you send the completed assignment, please outline any gotchas that the end user may experience.  In other words, what instructions / explanations can you provide to ensure that the end user does not break what you've built?

My Notes:
* I put all of the javascript inside of the HTML file. I thought, for reviewing purposes, that it might be easier to follow along that way.
* I put a lot of notes in the code so you could see where my head was at. 
* If you don't feel like cloning this locally, you can see a working example here: http://s130859622.onlinehome.us/mi-demo/demo.html?zip_code=10933&date=07/22/2015
* I threw a quickly thrown together media query in the CSS to make it responsive for a mobile device.
* The instructions did not say if I should be using tables, so I assumed modern day HTML/CSS was sufficient. I hope that is the case. I am happy to provide a mockup using table tags if need be.

My Gotchas:
* It is important to stress that both a valid, 5 digit numeric zip code and valid date are required to be appended to the URL. The expected date format is MM/DD/YYYY. At the end of your HTML file, the user should append something like hello-world.html?zip_code=94597&date=07/07/2015

* The order of the URL paramaters is very important. IE: the zip_code must be appended to the URL followed by the date, and not vice versa. 
**INVALID: hello-world.html?date=07/07/2015&zip_code=94597
**VALID: hello-world.html?zip_code=94597&date=07/07/2015

The 10 day forecast endoint does have contain any zip code data, so we have to first hit the geolookup end point with the zip code. This allows us to find the city name, and then we can use that city name to display the appropriate data from the 10 day forecast end point.
* geolookup endpoint: http://www.wunderground.com/weather/api/d/docs?d=data/geolookup
* forecast10day endpoint: http://www.wunderground.com/weather/api/d/docs?d=data/forecast10day

* The 10 day forecast endpoint contains weather data starting from the present date and the following 9 days. If you enter a date paramater that fell before the present date, or a date greater than 10 days from now, the page will not render any HTML.

* If you enter an invalid zip code, the page will not render any HTML, even if you enter a valid date.
* In the 10dayforecast endpoint, I didn't realize that the state must also be passed into the URL. I had /CA/ hardcoded into the URL in the code, but cities outside of the state of California would not break the script, IE: /CA/Johnson.json would render correct weather data. Johnson is a city in NY. When I entered a city name that was located in multiple states, the script would break. That is when I realized I needed to also pass the state in the URL. This was a personal "gotcha", but might be worth sending over to Weather Underground as a bug.
