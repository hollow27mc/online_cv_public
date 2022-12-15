---
name: Final Project Part 3
author: Trevin Kurniawan
tools: [Python, HTML, vega-lite]
description: This project showcases crashes in the city of Chicago

remote_projects:
   -online_cv_public

custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
# Crash Reports in Chicago

This project is based on a dataset from the police department of Chicago. It shows many records and details of car crashes that happened in the city of Chicago and this is the raw URL of the dataset.
[Car Crashes in Chicago](https://raw.githubusercontent.com/hollow27mc/IS445-Final-Project/main/Traffic_Crashes_-_Crashes.csv) 

# Contextual and Interactive Visualizations

We will be using vega-lite to plot the count of car crashes in different weather conditions. We are also going to be using a bar graph; this visualization will showcase the trend of car crashes according to the weather conditions.

---
<vegachart schema-url="{{ site.baseurl }}/assets/json/weatherCrashes.json" style="width: 100%"></vegachart>
---
The visualization below utilizes vega-lite again to plot the count of car crashes in different speed limits. We will again be using a bar graph; this visualization showcase the trend of car crashes in 30mph speed limit roads.
---
<vegachart schema-url="{{ site.baseurl }}/assets/json/speedlimit.json" style="width: 100%"></vegachart>
---
The next visualization also uses vega-lite. It showcases the amount of car that crashes according to the month and street direction of the accident. User can click and choose the direction (North, East, West and South) and also the month (1 - 12).
The visualization will show the amount of car crashes during the month by using colors, Dark Blue will be the highest amount of crashes and Light Green means that it has the least amount of crashes.
---
<vegachart schema-url="{{ site.baseurl }}/assets/json/Direction_crashes.json" style="width: 100%"></vegachart>
