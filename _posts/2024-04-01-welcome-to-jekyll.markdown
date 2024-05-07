<link rel="stylesheet" href="/assets/custom.css">


Then we divided individuals into two groups based on their mode of transportation: those who travel by car and those who use other transportation modes. An interactive plot was then created to examine differences in fare type, travel purpose, and the days of the week people travel.
<iframe src="/assets/interactive_plot.html"
    sandbox="allow-same-origin allow-scripts"
    width="100%"
    height="500"
    scrolling="no"
    seamless="seamless"
    frameborder="0">
</iframe>
Based on the interactive comparison plot, here we can see:

Fare Type: The majority of travelers either pay full fare or travel for free. There are consistently more travelers in each category who choose other modes over traveling by car. Notably, there is a higher proportion of disabled individuals opting for modes other than cars.

Travel Purpose: A significant number of people travel for Home-Based Other (HBO) purposes. In every category, the number of individuals using modes other than cars exceeds those who travel by car.

Day of the Week: Car users typically travel on weekends, with fewer choosing to travel on Mondays. Conversely, those who use other modes prefer to travel on weekdays, particularly on Fridays.



Our first plot looks at the different types fuel used in cars over time. Here we can see that petrol cars are overwhelmingly the most used cars. We have to remember, this dataset only goes from 2012 to 2015, so electric cars weren't as prevalant as a commuter car at this time.

<iframe src="/assets/over_time.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> </iframe> In this second plot, we analyzed the amount of CO2 emissions for each fuel type. We researched and found the UK government has a few different estimates for CO2 emissions of the different fuel types. These are averaged with 7600 miles over a year, so we have converted them to kg per meter. We see on this plot that the average CO2 emissions is highest for diesel LGVs, which are for light goods vehicles or vans. This makes sense, since bigger vehicles tend to have bigger emissions. We can also see that hybrid cars emit much less CO2 than the other fuel types. In theory, an electric vehicle doesn't emit any CO2, when not taking the cars manufacturing into account. <iframe src="/assets/emissions_per_trip.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> </iframe> This third plot is a histogram showing the counts of trips within an amount of CO2 emissions. We can see on the plot that most of the trips are in the "lower" end of the emission spectrum. However the highest emission in this bin is still almost 1400 kg/km. <iframe src="/assets/emissions_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> </iframe> This plot can be used to compare to the former, since it is a histogram showing the distances each trip has (in meters). We can see that most commuters only travel between a few meters and a little over 4 km. So most people probably work within this distance. <iframe src="/assets/distances_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> </iframe>
