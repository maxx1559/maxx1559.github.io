<link rel="stylesheet" href="/assets/custom.css">


We divided individuals into two groups based on their mode of transportation: those who travel by car and those who use other transportation modes. An interactive plot was then created to examine differences in fare type, travel purpose, and the days of the week people travel.
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

<iframe src="/assets/over_time.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> 
</iframe> 

In this second plot, we analyzed the amount of CO2 emissions for each fuel type. We researched and found the UK government has a few different estimates for CO2 emissions of the different fuel types. These are averaged with 7600 miles over a year, so we have converted them to kg per meter. We see on this plot that the average CO2 emissions is highest for diesel LGVs, which are for light goods vehicles or vans. This makes sense, since bigger vehicles tend to have bigger emissions. We can also see that hybrid cars emit much less CO2 than the other fuel types. In theory, an electric vehicle doesn't emit any CO2, when not taking the cars manufacturing into account. 
<iframe src="/assets/emission_per_trip.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> 
</iframe> 

This third plot is a histogram showing the counts of trips within an amount of CO2 emissions. We can see on the plot that most of the trips are in the "lower" end of the emission spectrum. However the highest emission in this bin is still almost 1400 kg/km. 
<iframe src="/assets/emissions_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe> 

This plot can be used to compare to the former, since it is a histogram showing the distances each trip has (in meters). We can see that most commuters only travel between a few meters and a little over 4 km. So most people probably work within this distance. 
<iframe src="/assets/distances_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe>

Understanding Urban Mobility in London through Cost and Time Efficiency

<iframe src="/assets/average_cost_per_kilometer.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe>

<iframe src="/assets/average_dur_per_kilometer.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe>
- Walking and Cycling: These modes show minimal costs, making them attractive for short urban trips. Walking, however, is the least time-efficient, reflecting a consistent decrease in speed over longer distances.
- Public Transport (PT): Public transport displays a sharp initial cost decrease, becoming more cost-effective over longer distances. However, its time efficiency only improves after initial delays, likely from waiting times and transfers, highlighting a trade-off between cost and convenience.
- Driving: Variable costs for driving could reflect congestion charges or increased fuel use over longer distances. In terms of time, driving starts less efficient for short urban trips but improves significantly over longer distances, suggesting its suitability for non-urban commutes.

Why These Visualizations Are Effective
These visualizations are effective for multiple reasons: they offer a holistic perspective by providing insights into both cost and time trade offs, crucial for informed travel decisions and urban planning. Their interactivity enhances user engagement and deepens understanding of how different travel modes perform across various distances. Furthermore, they reveal scalable insights that are applicable not only to individual decision-making but also to broader policy considerations, especially in infrastructure development and environmental strategies.

Conclusion: Balancing Cost, Time, and Environmental Considerations
The story depicted by these plots highlights the trade-offs between cost, time, and environmental impact. It shows that while walking and cycling are cost-effective and environmentally friendly for shorter distances, public transport and driving may be better suited for longer distances, depending on specific needs. The data suggests potential areas for improvement in public transport to make it a more appealing choice for shorter distances. This comprehensive analysis supports more informed decisions for commuters, urban planners, and policymakers, driving towards more sustainable and efficient transportation solutions in London.
