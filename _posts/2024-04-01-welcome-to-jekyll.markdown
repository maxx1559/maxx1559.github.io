<link rel="stylesheet" href="/assets/custom.css">

<h2>Environmental Impact of Commuting in London</h2>
We've analyzed a dataset containing the different commuter trips people in London take to work to detect a pattern based on gathering all travelling data of people located in New York.
<h3>1. The comparison between people who travel by car or other modes</h3>
We firstly divided individuals into two groups based on their mode of transportation: those who travel by car and those who use other transportation modes, mainly to see why people choose to travel by car or other modes. We assume travelling by car is the least environmental-friendly way. An interactive plot was then created to examine differences in fare type, travel purpose, and the days of the week people travel.
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

Travel Purpose: A significant number of people travel for HBO (Home-Based Other) purposes. In every category, the number of individuals using modes other than cars exceeds those who travel by car.

Day of the Week: Car users typically travel on weekends, with fewer choosing to travel on Mondays. Conversely, those who use other modes prefer to travel on weekdays, particularly on Fridays.

Overall, most of people choose to travel by car for HBO reasons and they prefer to travel on weekends.

<h3>2. The carbon dioxide emission for different travel types</h3>

Our first plot looks at the different types fuel used in cars over time. Here we can see that petrol cars are overwhelmingly the most used cars. We have to remember, this dataset only goes from 2012 to 2015, so electric cars weren't as prevalant as a commuter car at this time.

<iframe src="/assets/over_time.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> 
</iframe> 

In this second plot, we analyzed the amount of CO2 emissions for each fuel type. We researched and found the UK government has a few different estimates for CO2 emissions of the different fuel types. These are averaged with 7600 miles over a year, so we have converted them to kg per meter. We see on this plot that the average CO2 emissions is highest for diesel LGVs, which are for light goods vehicles or vans. This makes sense, since bigger vehicles tend to have bigger emissions. We can also see that hybrid cars emit much less CO2 than the other fuel types. In theory, an electric vehicle doesn't emit any CO2, when not taking the cars manufacturing into account. 
<iframe src="/assets/emission_per_trip.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0"> 
</iframe> 

This third plot is a histogram showing the counts of trips within an amount of CO2 emissions. We can see on the plot that most of the trips are in the "lower" end of the emission spectrum. However the highest emission in this bin is still 675 kg/km. 
<iframe src="/assets/emissions_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe> 

This plot can be used to compare to the former, since it is a histogram showing the distances each trip has (in meters). We can see that most commuters only travel between a few meters and a little over 4 km. So most people probably work within this distance. 
<iframe src="/assets/distances_histogram.html" sandbox="allow-same-origin allow-scripts" width="100%" height="500" scrolling="no" seamless="seamless" frameborder="0">
</iframe>

<h3>3.Understanding Urban Mobility in London through Cost and Time Efficiency</h3>
    
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



##Explainer Notebook:
# **Final Project - CO2 Emissions and Commuting in London**
**The central idea behind our final project**
The idea is to analyze how efficiently people can commute in London while considering their environmental footprint and how these factors match up with their actual commuting choices.

**Dataset Needed:**
The dataset below with 36 variables on 81,086 trips, covering different transport modes, costs, durations, personal demographics, and environmental impacts.


```python
import pandas as pd
df = pd.read_csv("dataset.csv")
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>trip_id</th>
      <th>household_id</th>
      <th>person_n</th>
      <th>trip_n</th>
      <th>travel_mode</th>
      <th>purpose</th>
      <th>fueltype</th>
      <th>faretype</th>
      <th>bus_scale</th>
      <th>survey_year</th>
      <th>...</th>
      <th>dur_pt_int_total</th>
      <th>dur_pt_int_waiting</th>
      <th>dur_pt_int_walking</th>
      <th>pt_n_interchanges</th>
      <th>dur_driving</th>
      <th>cost_transit</th>
      <th>cost_driving_total</th>
      <th>cost_driving_fuel</th>
      <th>cost_driving_con_charge</th>
      <th>driving_traffic_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.052222</td>
      <td>1.5</td>
      <td>0.14</td>
      <td>0.14</td>
      <td>0.0</td>
      <td>0.111702</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.059444</td>
      <td>1.5</td>
      <td>0.15</td>
      <td>0.15</td>
      <td>0.0</td>
      <td>0.112150</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.236667</td>
      <td>1.5</td>
      <td>0.79</td>
      <td>0.79</td>
      <td>0.0</td>
      <td>0.203052</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.233333</td>
      <td>1.5</td>
      <td>0.78</td>
      <td>0.78</td>
      <td>0.0</td>
      <td>0.160714</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>dis</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.229167</td>
      <td>1.5</td>
      <td>0.78</td>
      <td>0.78</td>
      <td>0.0</td>
      <td>0.130909</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>81081</th>
      <td>81081</td>
      <td>17615</td>
      <td>0</td>
      <td>0</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.216667</td>
      <td>0.197222</td>
      <td>0.019444</td>
      <td>2</td>
      <td>0.859722</td>
      <td>4.3</td>
      <td>2.48</td>
      <td>2.48</td>
      <td>0.0</td>
      <td>0.402262</td>
    </tr>
    <tr>
      <th>81082</th>
      <td>81082</td>
      <td>17615</td>
      <td>0</td>
      <td>2</td>
      <td>drive</td>
      <td>NHBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.183333</td>
      <td>0.160278</td>
      <td>0.023056</td>
      <td>2</td>
      <td>0.925833</td>
      <td>4.3</td>
      <td>2.53</td>
      <td>2.53</td>
      <td>0.0</td>
      <td>0.503750</td>
    </tr>
    <tr>
      <th>81083</th>
      <td>81083</td>
      <td>17615</td>
      <td>0</td>
      <td>3</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.112500</td>
      <td>1.5</td>
      <td>0.32</td>
      <td>0.32</td>
      <td>0.0</td>
      <td>0.234568</td>
    </tr>
    <tr>
      <th>81084</th>
      <td>81084</td>
      <td>17615</td>
      <td>1</td>
      <td>0</td>
      <td>pt</td>
      <td>HBW</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.250000</td>
      <td>0.230556</td>
      <td>0.019444</td>
      <td>2</td>
      <td>1.121944</td>
      <td>4.4</td>
      <td>12.88</td>
      <td>2.38</td>
      <td>10.5</td>
      <td>0.760832</td>
    </tr>
    <tr>
      <th>81085</th>
      <td>81085</td>
      <td>17615</td>
      <td>1</td>
      <td>1</td>
      <td>pt</td>
      <td>HBW</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.100000</td>
      <td>0.079167</td>
      <td>0.020833</td>
      <td>1</td>
      <td>0.941389</td>
      <td>5.9</td>
      <td>2.38</td>
      <td>2.38</td>
      <td>0.0</td>
      <td>0.652995</td>
    </tr>
  </tbody>
</table>
<p>81086 rows × 36 columns</p>
</div>



# **Commute Efficiency, Environmental Impact, and Preference**

**Objective:** Evaluate how commuters' preferences for transport modes align with the efficiency and environmental impact of those modes.

**Why is this interesting**
This is compelling because it touches on everyday decisions that affect personal time, finances, urban planning, and the environment. Understanding these dynamics can help in promoting sustainable transport policies, improving city infrastructure, and advocating for changes in commuter behavior.

**End goal**
The end goal for this project, is to be able to see the impact of commuting on the environment, and whether or not commuters in London can choose to travel more environmentally friendly. 


**Preliminary data analysis**

The dataset's file size is almost 15 MBs, has 81086 rows and 36 columns.

The date range of the survey year column is from 2012 to 2015.


```python
import matplotlib.pyplot as plt
fueltype_count = df["fueltype"].value_counts()
plt.figure(figsize=(3,3))
fueltype_count.plot(kind="bar")
plt.xlabel("Fuel type")
plt.ylabel("Occurences")
plt.title("Occurences of each fueltype of transport in London")
plt.show()
```


    
![png](/assets/Explainer%20Notebook_files/Explainer%20Notebook_4_0.png)
    



```python
travelmode_count = df["travel_mode"].value_counts()
plt.figure(figsize=(3,3))
travelmode_count.plot(kind="bar")
plt.xlabel("Travel Mode")
plt.ylabel("Occurences")
plt.title("Occurences of each mode of transport in London")
plt.show()
# drive is cars, pt is public transport, walk is walking and cycle is a bike
```


    
![png](/assets/Explainer%20Notebook_files/Explainer%20Notebook_5_0.png)
    



```python
year_counts = df["travel_year"].value_counts()
print("Year with most trips: ", year_counts.index[0],"\n")
print("Year with least trips: ", year_counts.index[-2], "\n")

sorted_year_count = year_counts.sort_index()
plt.figure(figsize=(3,3))
sorted_year_count.plot(kind="bar")
plt.title("Trips by year")
plt.xlabel("Year")
plt.ylabel("Amount of trips")
plt.show()
```

    Year with most trips:  2013 
    
    Year with least trips:  2012 
    
    


    
![png](/assets/Explainer%20Notebook_files/Explainer%20Notebook_6_1.png)
    


Through our exploratory analysis we noticed a few different things about the dataset. For example, clearly the dataset doesn't fully cover the year 2015.
Also, driving is clearly the most popular type of commuting. Specifically, driving with petrol cars. 

**Analysis**

We made several different analyses of the dataset.



```python
# Update emissions per meter calculations based on 7,600 miles per year (about 12,231 kilometers)
#Based on values from https://www.ageco.co.uk/useful-articles/car/what-are-the-co2-emissions-of-my-car/
# and https://www.eea.europa.eu/highlights/average-co2-emissions-from-new-cars-vans-2019
emissions_per_km = {
    'Petrol_Car': 1749 / 12231,  # kg per km
    'Diesel_Car': 2006 / 12231,
    'Hybrid_Car': (1544 + 429) / 2 / 12231,  # Average of two hybrid types
    'Plug-in_Hybrid': 429 / 12231,
    'Electric_Car': 0,  # Adding Electric Car with 0kg emissions
    'Petrol_LGV': 147.3 / 1000,  # Convert g/km to kg/km
    'Diesel_LGV': 161.2 / 1000
}
mean_emissions = sum(emissions_per_km.values()) / len(emissions_per_km)
emissions_per_km.update({
    'Average_Car': mean_emissions
})
# Calculate CO2 emissions for each row in the dataset
df['co2_emissions'] = df.apply(lambda row: emissions_per_km.get(row['fueltype'], 0) * row['distance'], axis=1)
# Group data by fuel type to calculate average emissions per meter
data = df[df["travel_mode"] == "drive"]
average_emissions = data.groupby('fueltype')['co2_emissions'].mean().reset_index()
from bokeh.plotting import figure, show, output_notebook,output_file
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.io import push_notebook

output_notebook()
output_file("emission_per_trip.html")

source = ColumnDataSource(data=average_emissions)
p = figure(x_range=average_emissions["fueltype"], 
           height=350, title="CO2 Emissions per Trip by Car Type",
           toolbar_location=None, tools="")

p.vbar(x='fueltype', top='co2_emissions', width=0.9, source=source)

# Add hover tool
hover = HoverTool()
hover.tooltips = [("Fuel Type", "@fueltype"), ("Avg CO2 Emissions (kg/trip)", "@co2_emissions")]
p.add_tools(hover)

# Styling
#p.xgrid.grid_line_color = None
p.y_range.start = 0

# Show the result
show(p)
```


```python
from bokeh.plotting import figure, show, output_notebook, output_file
from bokeh.models import ColumnDataSource, Slider, CustomJS, HoverTool
from bokeh.layouts import column
from bokeh.io import push_notebook
import numpy as np

# Example data (replace this with your actual CO2 emissions data)
co2_emissions = df[df["travel_mode"] == "drive"]
co2_emissions = co2_emissions["co2_emissions"]
# Initial histogram setup
hist, edges = np.histogram(co2_emissions, bins=10)

# Create a ColumnDataSource, include bin edges for tooltips
source = ColumnDataSource(data={
    'top': hist, 
    'left': edges[:-1], 
    'right': edges[1:],
    'bin_min': edges[:-1],
    'bin_max': edges[1:]
})

# Create a figure
p = figure(height=350, title="CO2 Emissions Histogram",
           tools="", x_range=[min(edges), max(edges)])

# Add quads to the figure
p.quad(bottom=0, top='top', left='left', right='right', source=source, line_color="white")

# Add hover tool to show bin range
hover = HoverTool(tooltips=[
    ("Bin Min", "@bin_min{0.0} kg/km"),
    ("Bin Max", "@bin_max{0.0} kg/km"),
    ("Count", "@top")
])
p.add_tools(hover)

# Slider for adjusting the bins
slider = Slider(start=5, end=50, value=10, step=1, title="Number of Bins")

# JavaScript to update the histogram based on the slider
callback = CustomJS(args=dict(source=source, slider=slider, all_emissions=co2_emissions), code="""
    var data = source.data;
    var bins = slider.value;
    var emissions = all_emissions;
    
    var hist = new Array(bins).fill(0);
    var min = Math.min(...emissions);
    var max = Math.max(...emissions);
    var width = (max - min) / bins;
    
    var edges = new Array(bins+1);
    
    for (var i = 0; i <= bins; i++) {
        edges[i] = min + i * width;
    }
    
    for (var j = 0; j < emissions.length; j++) {
        var index = Math.floor((emissions[j] - min) / width);
        if (index >= bins) { index = bins - 1; }
        hist[index]++;
    }
    
    data['top'] = hist;
    data['left'] = edges.slice(0, bins);
    data['right'] = edges.slice(1, bins+1);
    data['bin_min'] = edges.slice(0, bins);  // Update bin_min
    data['bin_max'] = edges.slice(1, bins+1);  // Update bin_max
    
    source.change.emit();
""")

slider.js_on_change('value', callback)

# Layout with slider and plot
layout = column(slider, p)

# Show the plot
output_notebook()
output_file("emissions_histogram.html")
show(layout)
```


```python
from bokeh.plotting import figure, show, output_notebook, output_file
from bokeh.models import ColumnDataSource, Slider, CustomJS, HoverTool
from bokeh.layouts import column
from bokeh.io import push_notebook
import numpy as np

# Example data (replace this with your actual CO2 emissions data)

distances = df[df["travel_mode"] == "drive"]
distances = df["distance"]
# Initial histogram setup
hist, edges = np.histogram(distances, bins=10)

# Create a ColumnDataSource, include bin edges for tooltips
source = ColumnDataSource(data={
    'top': hist, 
    'left': edges[:-1], 
    'right': edges[1:],
    'bin_min': edges[:-1],
    'bin_max': edges[1:]
})

# Create a figure
p = figure(height=350, title="Distance Histogram",
           tools="", x_range=[min(edges), max(edges)])

# Add quads to the figure
p.quad(bottom=0, top='top', left='left', right='right', source=source, line_color="white")

# Add hover tool to show bin range
hover = HoverTool(tooltips=[
    ("Bin Min", "@bin_min{0.0} m"),
    ("Bin Max", "@bin_max{0.0} m"),
    ("Count", "@top")
])
p.add_tools(hover)

# Slider for adjusting the bins
slider = Slider(start=5, end=50, value=10, step=1, title="Number of Bins")

# JavaScript to update the histogram based on the slider
callback = CustomJS(args=dict(source=source, slider=slider, all_emissions=distances), code="""
    var data = source.data;
    var bins = slider.value;
    var emissions = all_emissions;
    
    var hist = new Array(bins).fill(0);
    var min = Math.min(...emissions);
    var max = Math.max(...emissions);
    var width = (max - min) / bins;
    
    var edges = new Array(bins+1);
    
    for (var i = 0; i <= bins; i++) {
        edges[i] = min + i * width;
    }
    
    for (var j = 0; j < emissions.length; j++) {
        var index = Math.floor((emissions[j] - min) / width);
        if (index >= bins) { index = bins - 1; }
        hist[index]++;
    }
    
    data['top'] = hist;
    data['left'] = edges.slice(0, bins);
    data['right'] = edges.slice(1, bins+1);
    data['bin_min'] = edges.slice(0, bins);  // Update bin_min
    data['bin_max'] = edges.slice(1, bins+1);  // Update bin_max
    
    source.change.emit();
""")

slider.js_on_change('value', callback)

# Layout with slider and plot
layout = column(slider, p)

# Show the plot
output_notebook()
output_file("distances_histogram.html")
show(layout)
```

**See the other notebooks for more of the analysis**

**Discussion**

In doing our analysis of the dataset, we found out we overshot with our original ideas. We wanted to be able to create maps and such, but the dataset had no geographical data, which resulted in us changing our idea of showing how londoners commuted and their environmental impact instead. 
In the end, we still think a final dashboard could be made, essentially mashing all our plots toghether, creating filters to impact the different visualizations.
We would have liked to look at more correlations to show the differences and impacts of the different columns on each other, as well as on our added columns, such as co2_emissions. 

**Contributions**

Sunnie: Travel fare type by mode plots

Max: Distance plots (histograms, time plot)

Dimasha: Plots for averages of cost, duration, distance, etc.




```python

```



**Max's Notebook:**

```python
import pandas as pd
```

**The central idea behind our final project**
The idea is to analyze how efficiently people can commute in London while considering their environmental footprint and how these factors match up with their actual commuting choices.

**Dataset Needed:**
The dataset below with 36 variables on 81,086 trips, covering different transport modes, costs, durations, personal demographics, and environmental impacts.


```python
df = pd.read_csv("dataset.csv")
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>trip_id</th>
      <th>household_id</th>
      <th>person_n</th>
      <th>trip_n</th>
      <th>travel_mode</th>
      <th>purpose</th>
      <th>fueltype</th>
      <th>faretype</th>
      <th>bus_scale</th>
      <th>survey_year</th>
      <th>...</th>
      <th>dur_pt_int_total</th>
      <th>dur_pt_int_waiting</th>
      <th>dur_pt_int_walking</th>
      <th>pt_n_interchanges</th>
      <th>dur_driving</th>
      <th>cost_transit</th>
      <th>cost_driving_total</th>
      <th>cost_driving_fuel</th>
      <th>cost_driving_con_charge</th>
      <th>driving_traffic_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.052222</td>
      <td>1.5</td>
      <td>0.14</td>
      <td>0.14</td>
      <td>0.0</td>
      <td>0.111702</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.059444</td>
      <td>1.5</td>
      <td>0.15</td>
      <td>0.15</td>
      <td>0.0</td>
      <td>0.112150</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.236667</td>
      <td>1.5</td>
      <td>0.79</td>
      <td>0.79</td>
      <td>0.0</td>
      <td>0.203052</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.233333</td>
      <td>1.5</td>
      <td>0.78</td>
      <td>0.78</td>
      <td>0.0</td>
      <td>0.160714</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Petrol_Car</td>
      <td>dis</td>
      <td>1.0</td>
      <td>1</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.229167</td>
      <td>1.5</td>
      <td>0.78</td>
      <td>0.78</td>
      <td>0.0</td>
      <td>0.130909</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>81081</th>
      <td>81081</td>
      <td>17615</td>
      <td>0</td>
      <td>0</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.216667</td>
      <td>0.197222</td>
      <td>0.019444</td>
      <td>2</td>
      <td>0.859722</td>
      <td>4.3</td>
      <td>2.48</td>
      <td>2.48</td>
      <td>0.0</td>
      <td>0.402262</td>
    </tr>
    <tr>
      <th>81082</th>
      <td>81082</td>
      <td>17615</td>
      <td>0</td>
      <td>2</td>
      <td>drive</td>
      <td>NHBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.183333</td>
      <td>0.160278</td>
      <td>0.023056</td>
      <td>2</td>
      <td>0.925833</td>
      <td>4.3</td>
      <td>2.53</td>
      <td>2.53</td>
      <td>0.0</td>
      <td>0.503750</td>
    </tr>
    <tr>
      <th>81083</th>
      <td>81083</td>
      <td>17615</td>
      <td>0</td>
      <td>3</td>
      <td>drive</td>
      <td>HBO</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0</td>
      <td>0.112500</td>
      <td>1.5</td>
      <td>0.32</td>
      <td>0.32</td>
      <td>0.0</td>
      <td>0.234568</td>
    </tr>
    <tr>
      <th>81084</th>
      <td>81084</td>
      <td>17615</td>
      <td>1</td>
      <td>0</td>
      <td>pt</td>
      <td>HBW</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.250000</td>
      <td>0.230556</td>
      <td>0.019444</td>
      <td>2</td>
      <td>1.121944</td>
      <td>4.4</td>
      <td>12.88</td>
      <td>2.38</td>
      <td>10.5</td>
      <td>0.760832</td>
    </tr>
    <tr>
      <th>81085</th>
      <td>81085</td>
      <td>17615</td>
      <td>1</td>
      <td>1</td>
      <td>pt</td>
      <td>HBW</td>
      <td>Average_Car</td>
      <td>full</td>
      <td>1.0</td>
      <td>3</td>
      <td>...</td>
      <td>0.100000</td>
      <td>0.079167</td>
      <td>0.020833</td>
      <td>1</td>
      <td>0.941389</td>
      <td>5.9</td>
      <td>2.38</td>
      <td>2.38</td>
      <td>0.0</td>
      <td>0.652995</td>
    </tr>
  </tbody>
</table>
<p>81086 rows × 36 columns</p>
</div>



# **Commute Efficiency, Environmental Impact, and Preference**

**Objective:** Evaluate how commuters' preferences for transport modes align with the efficiency and environmental impact of those modes.

**Analysis:**
- *Efficiency and Environmental Scoring:* Develop a composite score that integrates efficiency (considering duration, cost) with environmental impact (based on fuel type and traffic congestion).
- *Preference Correlation:* Analyze how this composite score correlates with the actual choices commuters make, considering the frequency of use for each mode.



**Why is this interesting**
This is compelling because it touches on everyday decisions that affect personal time, finances, urban planning, and the environment. Understanding these dynamics can help in promoting sustainable transport policies, improving city infrastructure, and advocating for changes in commuter behavior.

**Visualization Mock-up:**
A mock-up for the visualization can be a multi-layered interactive dashboard that combines a map of London with filters for demographics and transport modes, and displays efficiency and environmental scores. It can include:
1. Map Visualization: A base map showing London with color-coded routes representing different efficiency and environmental impact levels.
2. Mode Selection: Buttons to filter by transport mode (walking, cycling, public transport, driving).
3. Demographic Filters: Sliders or dropdowns for filtering by age, gender, and car ownership.
4. Scoring Display: A sidebar displaying efficiency and environmental impact scores, dynamically updating based on the selected filters.
5. Preference Indicators: Graphs beside the map showing the popularity of each mode against its efficiency and environmental score.

**Genre of Visualization:**
The genre of this visualization is an "Interactive Dashboard," as it allows for active engagement from users to explore the data from multiple perspectives. It falls under the category of "Data Exploration," encouraging the user to form their own hypotheses and conclusions.

**Why the Genre Fits the Story:**
An interactive dashboard is ideal for this story because it can accommodate the complexity and multi-dimensionality of the data. It allows users to:

- See the big picture of transportation in London.
- Drill down to understand individual commuting decisions.
- Explore hypothetical scenarios by adjusting parameters (e.g., what if - more people cycled?).
- Encourage discovery and personalized insights, which is more engaging than static visualizations.


```python
print(len(df.columns))
```

    36
    

**Preliminary data analysis**

The datasets file size is almost 15 MBs, has 81086 rows and 36 columns.

The date range of the survey year column is from 2012 to 2015


```python
import matplotlib.pyplot as plt
fueltype_count = df["fueltype"].value_counts()
plt.figure(figsize=(5,4))
fueltype_count.plot(kind="bar")
plt.xlabel("Fuel type")
plt.ylabel("Occurences")
plt.title("Occurences of each fueltype of transport in London")
plt.show()
```


    
![png](/assets/Project%20Assignment%201_files/Project%20Assignment%201_7_0.png)
    



```python
travelmode_count = df["travel_mode"].value_counts()
plt.figure(figsize=(5,4))
travelmode_count.plot(kind="bar")
plt.xlabel("Travel Mode")
plt.ylabel("Occurences")
plt.title("Occurences of each mode of transport in London")
plt.show()
# drive is cars, pt is public transport, walk is walking and cycle is a bike
```


    
![png](/assets/Project%20Assignment%201_files/Project%20Assignment%201_8_0.png)
    



```python
year_counts = df["travel_year"].value_counts()
print("Year with most trips: ", year_counts.index[0],"\n")
print("Year with least trips: ", year_counts.index[-2], "\n")

sorted_year_count = year_counts.sort_index()
plt.figure()
sorted_year_count.plot(kind="bar")
plt.title("Trips by year")
plt.xlabel("Year")
plt.ylabel("Amount of trips")
plt.show()
```

    Year with most trips:  2013 
    
    Year with least trips:  2012 
    
    


    
![png](/assets/Project%20Assignment%201_files/Project%20Assignment%201_9_1.png)
    



```python
df["Date"] = df["travel_date"].astype(str) + "/" + df["travel_month"].astype(str) + "/" + df["travel_year"].astype(str)
df["Date"] = pd.to_datetime(df["Date"], format="%d/%m/%Y", dayfirst=True)
print(df["Date"])
```

    0       2012-04-01
    1       2012-04-01
    2       2012-04-01
    3       2012-04-01
    4       2012-04-01
               ...    
    81081   2015-03-31
    81082   2015-03-31
    81083   2015-03-31
    81084   2015-03-31
    81085   2015-03-31
    Name: Date, Length: 81086, dtype: datetime64[ns]
    


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pandas.api.types import CategoricalDtype
from bokeh.plotting import figure, show
from bokeh.models import ColumnDataSource, FactorRange, Legend,RangeTool
from bokeh.palettes import Spectral11, Category20
from bokeh.transform import linear_cmap, jitter
from bokeh.io import output_notebook, output_file
from bokeh.layouts import column
df_grouped = df.groupby(by=["Date", "fueltype"]).size()

# Group by category and year and count the number of incidents
category_grouped_counts = df.groupby(['fueltype', 'Date']).size().reset_index(name='Counts')

# Calculate the total counts for each category over the entire period
total_counts_by_category = category_grouped_counts.groupby('fueltype')['Counts'].sum().reset_index(name='TotalCounts')

# Merge the total counts back to the yearly data
merged_data = category_grouped_counts.merge(total_counts_by_category, on='fueltype')

# Normalize the data by dividing the yearly counts by total counts for each category
merged_data['Normalized'] = merged_data['Counts'] / merged_data['TotalCounts']

# Pivot the table to have years as rows and categories as columns
normalized_pivot = merged_data.pivot(index='Date', columns='fueltype', values='Counts').fillna(0)
sorted_categories = normalized_pivot.reindex(sorted(normalized_pivot.columns), axis=1)

dates = sorted_categories.index.values

sorted_categories.reset_index(inplace = True)


p = figure(height=300, width=800, tools="xpan", toolbar_location=None,
           x_axis_type="datetime", x_axis_location="above",
           background_fill_color="#efefef", x_range=(dates[0], dates[1081]))

fueltypes = df["fueltype"].unique()
type_to_color = {type: Category20[len(fueltypes)][i] for i, type in enumerate(fueltypes)}
items = []
lines = {}

for i,type in enumerate(fueltypes):
    source = ColumnDataSource(data=dict(date=dates, count=sorted_categories[type]))
    lines = p.line('date', 'count', source=source, line_color=type_to_color[type])
    items.append((type, [lines]))

p.yaxis.axis_label = 'Incidents'

select = figure(title="Drag the middle and edges of the selection box to change the range above",
                height=130, width=800, y_range=p.y_range,
                x_axis_type="datetime", y_axis_type=None,
                tools="", toolbar_location=None, background_fill_color="#efefef")

range_tool = RangeTool(x_range=p.x_range)
range_tool.overlay.fill_color = "navy"
range_tool.overlay.fill_alpha = 0.2

select.line('date', 'count', source=source)
select.ygrid.grid_line_color = None
select.add_tools(range_tool)

legend = Legend(items=items, location=[0,-30]) ## figure where to add it
p.add_layout(legend, 'right') ## figure where to add it
### if you read the guide, it will make sense
p.legend.click_policy="mute"
output_notebook()
output_file("over_time.html")
show(column(p, select))
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="e93e15b8-2804-4dc2-bad2-8d1b7e54839e">Loading BokehJS ...</span>
</div>







<div id="d481af78-9a49-4596-94dd-1254d892dc0d" data-root-id="p3318" style="display: contents;"></div>





## Change over time
This plot above, shows that the amount of trips changed often, most likely as a result of vacations or weekends, meaning less commuting. However a clear "winner" still prevails, the petrol car. 


```python
df["total_dur"] = df["dur_walking"] + df["dur_cycling"] + df["dur_pt_total"] + df["dur_driving"]
print(df.total_dur)
df["total_cost"] = df.cost_transit + df.cost_driving_total
print(df.total_cost)
```

    0        0.511944
    1        0.478333
    2        2.042500
    3        2.120833
    4        2.014167
               ...   
    81081    6.669722
    81082    6.082222
    81083    1.070000
    81084    6.329722
    81085    6.111111
    Name: total_dur, Length: 81086, dtype: float64
    0         1.64
    1         1.65
    2         2.29
    3         2.28
    4         2.28
             ...  
    81081     6.78
    81082     6.83
    81083     1.82
    81084    17.28
    81085     8.28
    Name: total_cost, Length: 81086, dtype: float64
    


```python
household_modes = df.groupby(by=['household_id','travel_mode']).size().reset_index(name='Counts')
household_counts = household_modes.groupby('travel_mode')['Counts'].sum().reset_index(name='TotalCounts')
print(household_counts)
```

      travel_mode  TotalCounts
    0       cycle         2405
    1       drive        35808
    2          pt        28605
    3        walk        14268
    


```python
plt.bar(household_counts.travel_mode,household_counts.TotalCounts,width=0.4)
plt.show()
```


    
![png](/assets/Project%20Assignment%201_files/Project%20Assignment%201_15_0.png)
    



```python
purpose_counts = df["purpose"].value_counts()
purpose_counts.plot(kind="bar")
plt.show()
```


    
![png](/assets/Project%20Assignment%201_files/Project%20Assignment%201_16_0.png)
    



```python
# Update emissions per meter calculations based on 7,600 miles per year (about 12,231 kilometers)
#Based on values from https://www.ageco.co.uk/useful-articles/car/what-are-the-co2-emissions-of-my-car/
# and https://www.eea.europa.eu/highlights/average-co2-emissions-from-new-cars-vans-2019
emissions_per_km = {
    'Petrol_Car': 1749 / 12231,  # kg per km
    'Diesel_Car': 2006 / 12231,
    'Hybrid_Car': (1544 + 429) / 2 / 12231,  # Average of two hybrid types
    'Plug-in_Hybrid': 429 / 12231,
    'Electric_Car': 0,  # Adding Electric Car with 0kg emissions
    'Petrol_LGV': 147.3 / 1000,  # Convert g/km to kg/km
    'Diesel_LGV': 161.2 / 1000
}
mean_emissions = sum(emissions_per_km.values()) / len(emissions_per_km)
emissions_per_km.update({
    'Average_Car': mean_emissions
})
# Calculate CO2 emissions for each row in the dataset
df['co2_emissions'] = df.apply(lambda row: emissions_per_km.get(row['fueltype'], 0) * row['distance'], axis=1)
# Group data by fuel type to calculate average emissions per meter
data = df[df["travel_mode"] == "drive"]
average_emissions = data.groupby('fueltype')['co2_emissions'].mean().reset_index()

```


```python
from bokeh.plotting import figure, show, output_notebook,output_file
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.io import push_notebook

output_notebook()
output_file("emission_per_trip.html")

source = ColumnDataSource(data=average_emissions)
p = figure(x_range=average_emissions["fueltype"], 
           height=350, title="CO2 Emissions per Trip by Car Type",
           toolbar_location=None, tools="")

p.vbar(x='fueltype', top='co2_emissions', width=0.9, source=source)

# Add hover tool
hover = HoverTool()
hover.tooltips = [("Fuel Type", "@fueltype"), ("Avg CO2 Emissions (kg/trip)", "@co2_emissions")]
p.add_tools(hover)

# Styling
#p.xgrid.grid_line_color = None
p.y_range.start = 0

# Show the result
show(p)
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="e2c693f5-e73c-47b1-bf94-aa27579cf4d5">Loading BokehJS ...</span>
</div>







<div id="c2275589-b293-4c64-99e9-7f51faf8e047" data-root-id="p3347" style="display: contents;"></div>





The above visualization was chosen because it can quickly at a glance give an idea of what contributes the most to emission in our commuter dataset. Here it is quite clearly the LGVs (presumebly "light goods vehicles" or vans) which pollute the most overall, but the vehicles using fossil fuels are not far behind. 


```python
from bokeh.plotting import figure, show, output_notebook, output_file
from bokeh.models import ColumnDataSource, Slider, CustomJS, HoverTool
from bokeh.layouts import column
from bokeh.io import push_notebook
import numpy as np

# Example data (replace this with your actual CO2 emissions data)
co2_emissions = df[df["travel_mode"] == "drive"]
co2_emissions = co2_emissions["co2_emissions"]
# Initial histogram setup
hist, edges = np.histogram(co2_emissions, bins=10)

# Create a ColumnDataSource, include bin edges for tooltips
source = ColumnDataSource(data={
    'top': hist, 
    'left': edges[:-1], 
    'right': edges[1:],
    'bin_min': edges[:-1],
    'bin_max': edges[1:]
})

# Create a figure
p = figure(height=350, title="CO2 Emissions Histogram",
           tools="", x_range=[min(edges), max(edges)])

# Add quads to the figure
p.quad(bottom=0, top='top', left='left', right='right', source=source, line_color="white")

# Add hover tool to show bin range
hover = HoverTool(tooltips=[
    ("Bin Min", "@bin_min{0.0} kg/km"),
    ("Bin Max", "@bin_max{0.0} kg/km"),
    ("Count", "@top")
])
p.add_tools(hover)

# Slider for adjusting the bins
slider = Slider(start=5, end=50, value=10, step=1, title="Number of Bins")

# JavaScript to update the histogram based on the slider
callback = CustomJS(args=dict(source=source, slider=slider, all_emissions=co2_emissions), code="""
    var data = source.data;
    var bins = slider.value;
    var emissions = all_emissions;
    
    var hist = new Array(bins).fill(0);
    var min = Math.min(...emissions);
    var max = Math.max(...emissions);
    var width = (max - min) / bins;
    
    var edges = new Array(bins+1);
    
    for (var i = 0; i <= bins; i++) {
        edges[i] = min + i * width;
    }
    
    for (var j = 0; j < emissions.length; j++) {
        var index = Math.floor((emissions[j] - min) / width);
        if (index >= bins) { index = bins - 1; }
        hist[index]++;
    }
    
    data['top'] = hist;
    data['left'] = edges.slice(0, bins);
    data['right'] = edges.slice(1, bins+1);
    data['bin_min'] = edges.slice(0, bins);  // Update bin_min
    data['bin_max'] = edges.slice(1, bins+1);  // Update bin_max
    
    source.change.emit();
""")

slider.js_on_change('value', callback)

# Layout with slider and plot
layout = column(slider, p)

# Show the plot
output_notebook()
output_file("emissions_histogram.html")
show(layout)
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="ca35c66c-7198-460f-b92f-6b0f80ca66e3">Loading BokehJS ...</span>
</div>







<div id="dd65fcb4-6654-450a-9312-d2fa01076ea1" data-root-id="p3423" style="display: contents;"></div>





This visualization was chosen to represent the amount of vehicles in each CO2 emission bracket. So a high amount of them are in the lower end of the spectrum, starting at 8.0 kg/km.


```python
sub_df = df[["co2_emissions","dur_driving"]]
print(sub_df)
corr_sub = sub_df.corr()
print(corr_sub)

```

           co2_emissions  dur_driving
    0         111.251901     0.052222
    1         111.251901     0.059444
    2         652.353691     0.236667
    3         652.353691     0.233333
    4         652.353691     0.229167
    ...              ...          ...
    81081    1639.747429     0.859722
    81082    1513.138913     0.925833
    81083     170.273830     0.112500
    81084    1354.042567     1.121944
    81085    1354.042567     0.941389
    
    [81086 rows x 2 columns]
                   co2_emissions  dur_driving
    co2_emissions       1.000000     0.901276
    dur_driving         0.901276     1.000000
    


```python
from bokeh.plotting import figure, show, output_notebook, output_file
from bokeh.models import ColumnDataSource, Slider, CustomJS, HoverTool
from bokeh.layouts import column
from bokeh.io import push_notebook
import numpy as np

# Example data (replace this with your actual CO2 emissions data)

distances = df[df["travel_mode"] == "drive"]
distances = df["distance"]
# Initial histogram setup
hist, edges = np.histogram(distances, bins=10)

# Create a ColumnDataSource, include bin edges for tooltips
source = ColumnDataSource(data={
    'top': hist, 
    'left': edges[:-1], 
    'right': edges[1:],
    'bin_min': edges[:-1],
    'bin_max': edges[1:]
})

# Create a figure
p = figure(height=350, title="Distance Histogram",
           tools="", x_range=[min(edges), max(edges)])

# Add quads to the figure
p.quad(bottom=0, top='top', left='left', right='right', source=source, line_color="white")

# Add hover tool to show bin range
hover = HoverTool(tooltips=[
    ("Bin Min", "@bin_min{0.0} m"),
    ("Bin Max", "@bin_max{0.0} m"),
    ("Count", "@top")
])
p.add_tools(hover)

# Slider for adjusting the bins
slider = Slider(start=5, end=50, value=10, step=1, title="Number of Bins")

# JavaScript to update the histogram based on the slider
callback = CustomJS(args=dict(source=source, slider=slider, all_emissions=distances), code="""
    var data = source.data;
    var bins = slider.value;
    var emissions = all_emissions;
    
    var hist = new Array(bins).fill(0);
    var min = Math.min(...emissions);
    var max = Math.max(...emissions);
    var width = (max - min) / bins;
    
    var edges = new Array(bins+1);
    
    for (var i = 0; i <= bins; i++) {
        edges[i] = min + i * width;
    }
    
    for (var j = 0; j < emissions.length; j++) {
        var index = Math.floor((emissions[j] - min) / width);
        if (index >= bins) { index = bins - 1; }
        hist[index]++;
    }
    
    data['top'] = hist;
    data['left'] = edges.slice(0, bins);
    data['right'] = edges.slice(1, bins+1);
    data['bin_min'] = edges.slice(0, bins);  // Update bin_min
    data['bin_max'] = edges.slice(1, bins+1);  // Update bin_max
    
    source.change.emit();
""")

slider.js_on_change('value', callback)

# Layout with slider and plot
layout = column(slider, p)

# Show the plot
output_notebook()
output_file("distances_histogram.html")
show(layout)
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="b39f390f-fbc0-4661-86a2-2b057fd27cb4">Loading BokehJS ...</span>
</div>







<div id="d05aea38-7f7c-49b4-a284-99835aaa9e82" data-root-id="p3475" style="display: contents;"></div>






```python

```

**Dimasha Notebook:**


```python
import pandas as pd
from bokeh.io import output_notebook, show
from bokeh.models import CheckboxButtonGroup, RangeSlider, ColumnDataSource
from bokeh.plotting import figure
from bokeh.layouts import column, row
from bokeh.transform import factor_cmap
from bokeh.palettes import Spectral4
from bokeh.palettes import Category10
from bokeh.io import output_notebook, show, output_file
from bokeh.application.handlers import FunctionHandler
from bokeh.application import Application
from bokeh.plotting import figure, show, output_notebook
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.layouts import gridplot
import pandas as pd
from bokeh.plotting import figure, show, output_notebook
from bokeh.layouts import gridplot
from bokeh.models import ColumnDataSource
from bokeh.palettes import Spectral4
from bokeh.models import Range1d  
from bokeh.plotting import figure, show, output_notebook
from bokeh.layouts import column
from bokeh.models import ColumnDataSource, HoverTool, PanTool, WheelZoomTool, BoxZoomTool, ResetTool, SaveTool
from bokeh.palettes import Spectral4

```


```python
df = pd.read_csv("dataset.csv")
df_filtered = df[['trip_id','travel_mode','purpose','travel_year','travel_month','age','female','distance','dur_walking','dur_cycling','dur_pt_total','dur_driving','cost_transit','cost_driving_total']]
df = df_filtered.copy()
```

Age_category columns 


```python
bins = [0, 18, 30, 55, 100]  
labels = ['Under 18', '18-30', '31-55', '56 and older']
df['age_group'] = pd.cut(df['age'], bins=bins, labels=labels, right=False)
```

Adding 2 new columns for pounds/kilometer and minutes/kilometers


```python
def calculate_pounds_per_km(row):
    if row['travel_mode'] == 'walk' or row['travel_mode'] == 'cycle':
        return 0  # Cost for walking and cycling is 0
    elif row['travel_mode'] == 'pt':
        return row['cost_transit'] / (row['distance'] * 0.001)  # Convert meters to kilometers
    elif row['travel_mode'] == 'drive':
        return row['cost_driving_total'] / (row['distance'] * 0.001)  # Convert meters to kilometers

def calculate_min_per_km(row):
    if row['travel_mode'] == 'walk':
        return (row['dur_walking'] * 60) / (row['distance'] * 0.001)  # Convert hours to minutes and meters to kilometers
    elif row['travel_mode'] == 'cycle':
        return (row['dur_cycling'] * 60) / (row['distance'] * 0.001)
    elif row['travel_mode'] == 'pt':
        return (row['dur_pt_total'] * 60) / (row['distance'] * 0.001)
    elif row['travel_mode'] == 'drive':
        return (row['dur_driving'] * 60) / (row['distance'] * 0.001)

# Applying these functions to each row of the DataFrame to create new columns
df['pounds_per_km'] = df.apply(calculate_pounds_per_km, axis=1)
df['min_per_km'] = df.apply(calculate_min_per_km, axis=1)
```

Plotting cost and duration vs distance


```python
output_notebook()  

modes = ['walk', 'cycle', 'pt', 'drive']
colors = ['blue', 'green', 'red', 'black']  

# ColumnDataSource for each mode
sources = {mode: ColumnDataSource(df[df['travel_mode'] == mode]) for mode in modes}

# Plot 1: Cost vs. Distance
p1 = figure(width=600, height=400, title="Cost Analysis per Kilometer by Travel Mode",
            x_axis_label="Distance (km)", y_axis_label="Cost (£/km)")

for mode, color in zip(modes, colors):
    p1.line(x='distance', y='pounds_per_km', line_width=2, color=color, legend_label=mode.capitalize(), source=sources[mode])
    p1.add_tools(HoverTool(tooltips=[("Mode", mode), ("Distance", "@distance"), ("Cost", "@pounds_per_km")]))

p1.legend.title = 'Travel Mode'
p1.legend.location = "top_left"

# Plot 2: Duration vs. Distance
p2 = figure(width=600, height=400, title="Duration Analysis per Kilometer by Travel Mode",
            x_axis_label="Distance (km)", y_axis_label="Duration (min/km)")

for mode, color in zip(modes, colors):
    p2.line(x='distance', y='min_per_km', line_width=2, color=color, legend_label=mode.capitalize(), source=sources[mode])
    p2.add_tools(HoverTool(tooltips=[("Mode", mode), ("Distance", "@distance"), ("Duration", "@min_per_km")]))

p2.legend.title = 'Travel Mode'
p2.legend.location = "top_left"

# Layout the plots in a grid
layout = gridplot([[p1], [p2]])

output_file("cost_per_kilometer.html")
# Show the plots
show(layout)
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="e158e0cd-9b18-4897-84fc-5919ed2a1dc9">Loading BokehJS ...</span>
</div>







<div id="c64c91c1-16af-4fb2-8b57-75bef2a113ea" data-root-id="p2341" style="display: contents;"></div>





This is a little messy so I will simplify the plots by showing only one average value for every 100 meters for the average cost/km and average duration/km for each transport mode: To do this, I will bin the data by 100 meters before calculaing the average. This way I can clean up the plots by reducing the number of data points and focusing on broader trends across distances.


```python
# distance bins of 100 meters
df['distance_bin'] = pd.cut(df['distance'], bins=range(0, int(df['distance'].max()) + 100, 100), right=False)

# Grouping by distance_bin and travel_mode, then calculating the mean
average_cost_per_km = df.groupby(['distance_bin', 'travel_mode']).agg({'pounds_per_km': 'mean'}).reset_index()
average_min_per_km = df.groupby(['distance_bin', 'travel_mode']).agg({'min_per_km': 'mean'}).reset_index()

# Converting 'distance_bin' to string for plotting (left edge of the bin as representative value)
average_cost_per_km['distance_bin'] = average_cost_per_km['distance_bin'].apply(lambda x: x.left)
average_min_per_km['distance_bin'] = average_min_per_km['distance_bin'].apply(lambda x: x.left)

#ColumnDataSources for the averages
source_cost = ColumnDataSource(average_cost_per_km)
source_duration = ColumnDataSource(average_min_per_km)

output_notebook()

# figures
p1 = figure(width=800, height=400, title="Average Cost per Kilometer by Travel Mode", x_axis_label="Distance (m)", y_axis_label="Average Cost (£/km)")
p2 = figure(width=800, height=400, title="Average Duration per Kilometer by Travel Mode", x_axis_label="Distance (m)", y_axis_label="Average Duration (min/km)")

modes = ['walk', 'cycle', 'pt', 'drive']
colors = ['blue', 'green', 'red', 'black']

# Ploting each mode
for mode, color in zip(modes, colors):
    mode_data_cost = average_cost_per_km[average_cost_per_km['travel_mode'] == mode]
    mode_data_duration = average_min_per_km[average_min_per_km['travel_mode'] == mode]
    p1.line(x='distance_bin', y='pounds_per_km', line_width=2, color=color, legend_label=mode.capitalize(), source=ColumnDataSource(mode_data_cost))
    p2.line(x='distance_bin', y='min_per_km', line_width=2, color=color, legend_label=mode.capitalize(), source=ColumnDataSource(mode_data_duration))

# legends
p1.legend.location = "top_right"
p2.legend.location = "top_right"

layout = gridplot([[p1], [p2]])
output_file("average_cost_per_kilometer.html")

# Show the plots
show(layout)
```

    C:\Users\maxhb\AppData\Local\Temp\ipykernel_32200\1418672189.py:5: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      average_cost_per_km = df.groupby(['distance_bin', 'travel_mode']).agg({'pounds_per_km': 'mean'}).reset_index()
    C:\Users\maxhb\AppData\Local\Temp\ipykernel_32200\1418672189.py:6: FutureWarning: The default of observed=False is deprecated and will be changed to True in a future version of pandas. Pass observed=False to retain current behavior or observed=True to adopt the future default and silence this warning.
      average_min_per_km = df.groupby(['distance_bin', 'travel_mode']).agg({'min_per_km': 'mean'}).reset_index()
    


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="c95229de-bf76-409e-856a-b8252f5b1ea8">Loading BokehJS ...</span>
</div>







<div id="d126b110-4342-49a9-8d46-fdb8db18e557" data-root-id="p2649" style="display: contents;"></div>





Trying to add some interactive features:


```python
output_notebook()

# Create ColumnDataSource for each mode for better interactivity
data_sources = {}
modes = ['walk', 'cycle', 'pt', 'drive']
colors = ['blue', 'green', 'red', 'black']

for mode in modes:
    data_sources[mode] = ColumnDataSource({
        'distance': average_cost_per_km[average_cost_per_km['travel_mode'] == mode]['distance_bin'],
        'cost': average_cost_per_km[average_cost_per_km['travel_mode'] == mode]['pounds_per_km'],
        'duration': average_min_per_km[average_min_per_km['travel_mode'] == mode]['min_per_km']
    })

# Plot 1: Average Cost per Kilometer
p1 = figure(width=800, height=400, title="Interactive Average Cost per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Cost (£/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")

# Plot 2: Average Duration per Kilometer
p2 = figure(width=800, height=400, title="Interactive Average Duration per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Duration (min/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")

# Adding lines with hover tool
for mode, color in zip(modes, colors):
    line1 = p1.line('distance', 'cost', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])
    line2 = p2.line('distance', 'duration', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])

    p1.add_tools(HoverTool(renderers=[line1], tooltips=[('Mode', mode.capitalize()), ('Distance', '@distance'), ('Cost', '@cost{0.2f}')], mode='vline'))
    p2.add_tools(HoverTool(renderers=[line2], tooltips=[('Mode', mode.capitalize()), ('Distance', '@distance'), ('Duration', '@duration{0.2f}')], mode='vline'))

# Configuring the legends to toggle line visibility
p1.legend.click_policy = "hide"
p2.legend.click_policy = "hide"


layout = column(p1, p2)
output_file("interactive_average_cost_per_kilometer.html")

show(layout)
```


<style>
    .bk-notebook-logo {
        display: block;
        width: 20px;
        height: 20px;
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABx0RVh0U29mdHdhcmUAQWRvYmUgRmlyZXdvcmtzIENTNui8sowAAAOkSURBVDiNjZRtaJVlGMd/1/08zzln5zjP1LWcU9N0NkN8m2CYjpgQYQXqSs0I84OLIC0hkEKoPtiH3gmKoiJDU7QpLgoLjLIQCpEsNJ1vqUOdO7ppbuec5+V+rj4ctwzd8IIbbi6u+8f1539dt3A78eXC7QizUF7gyV1fD1Yqg4JWz84yffhm0qkFqBogB9rM8tZdtwVsPUhWhGcFJngGeWrPzHm5oaMmkfEg1usvLFyc8jLRqDOMru7AyC8saQr7GG7f5fvDeH7Ej8CM66nIF+8yngt6HWaKh7k49Soy9nXurCi1o3qUbS3zWfrYeQDTB/Qj6kX6Ybhw4B+bOYoLKCC9H3Nu/leUTZ1JdRWkkn2ldcCamzrcf47KKXdAJllSlxAOkRgyHsGC/zRday5Qld9DyoM4/q/rUoy/CXh3jzOu3bHUVZeU+DEn8FInkPBFlu3+nW3Nw0mk6vCDiWg8CeJaxEwuHS3+z5RgY+YBR6V1Z1nxSOfoaPa4LASWxxdNp+VWTk7+4vzaou8v8PN+xo+KY2xsw6une2frhw05CTYOmQvsEhjhWjn0bmXPjpE1+kplmmkP3suftwTubK9Vq22qKmrBhpY4jvd5afdRA3wGjFAgcnTK2s4hY0/GPNIb0nErGMCRxWOOX64Z8RAC4oCXdklmEvcL8o0BfkNK4lUg9HTl+oPlQxdNo3Mg4Nv175e/1LDGzZen30MEjRUtmXSfiTVu1kK8W4txyV6BMKlbgk3lMwYCiusNy9fVfvvwMxv8Ynl6vxoByANLTWplvuj/nF9m2+PDtt1eiHPBr1oIfhCChQMBw6Aw0UulqTKZdfVvfG7VcfIqLG9bcldL/+pdWTLxLUy8Qq38heUIjh4XlzZxzQm19lLFlr8vdQ97rjZVOLf8nclzckbcD4wxXMidpX30sFd37Fv/GtwwhzhxGVAprjbg0gCAEeIgwCZyTV2Z1REEW8O4py0wsjeloKoMr6iCY6dP92H6Vw/oTyICIthibxjm/DfN9lVz8IqtqKYLUXfoKVMVQVVJOElGjrnnUt9T9wbgp8AyYKaGlqingHZU/uG2NTZSVqwHQTWkx9hxjkpWDaCg6Ckj5qebgBVbT3V3NNXMSiWSDdGV3hrtzla7J+duwPOToIg42ChPQOQjspnSlp1V+Gjdged7+8UN5CRAV7a5EdFNwCjEaBR27b3W890TE7g24NAP/mMDXRWrGoFPQI9ls/MWO2dWFAar/xcOIImbbpA3zgAAAABJRU5ErkJggg==);
    }
</style>
<div>
    <a href="https://bokeh.org" target="_blank" class="bk-notebook-logo"></a>
    <span id="c8be51a6-08d5-4c69-9392-86dc4c31a2b5">Loading BokehJS ...</span>
</div>







<div id="cac28011-9857-41da-82e4-4e33dd84c7ec" data-root-id="p2866" style="display: contents;"></div>





To adjust the y-axis scale I will use a dynamic scaling method based on the quantiles of the data to exclude extreme values. This can help in focusing the plot on the range where most of the data lies, making it easier to interpret.

Here I am adjusting the range of the plot to cover up to the 95th percentile of the data:



```python
quantile_95_cost = df['pounds_per_km'].quantile(0.95)  

p1 = figure(width=800, height=400, title="Interactive Average Cost per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Cost (£/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")

# Setting the y-axis range dynamically
p1.y_range = Range1d(0, quantile_95_cost)

for mode, color in zip(modes, colors):
    p1.line('distance', 'cost', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])
output_file("cost_per_kilometer.html")

show(p1)

quantile_95_duration = average_min_per_km['min_per_km'].quantile(0.95)  # Get the 95th percentile for duration

p2 = figure(width=800, height=400, title="Interactive Average Duration per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Duration (min/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")

# Setting the y-axis range dynamically for the duration plot
p2.y_range = Range1d(0, quantile_95_duration)

for mode, color in zip(modes, colors):
    p2.line('distance', 'duration', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])

show(p2)


```



<div id="abbcb304-3f3c-4f94-94fb-fa459f39350c" data-root-id="p2892" style="display: contents;"></div>







<div id="ff1a5fe4-295c-4f8d-980d-3584c1e82218" data-root-id="p2991" style="display: contents;"></div>






```python
from bokeh.plotting import figure, show
from bokeh.models import HoverTool, ColumnDataSource, Range1d

quantile_95_cost = df['pounds_per_km'].quantile(0.95)
quantile_95_duration = average_min_per_km['min_per_km'].quantile(0.95)

# figure for cost
p1 = figure(width=800, height=400, title="Interactive Average Cost per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Cost (£/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")
p1.y_range = Range1d(0, quantile_95_cost)

#figure for duration
p2 = figure(width=800, height=400, title="Interactive Average Duration per Kilometer by Travel Mode",
            x_axis_label="Distance (m)", y_axis_label="Average Duration (min/km)",
            tools="pan,wheel_zoom,box_zoom,reset,save")
p2.y_range = Range1d(0, quantile_95_duration)

# lines and hover tools for each mode
for mode, color in zip(modes, colors):
    p1.line('distance', 'cost', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])
    p2.line('distance', 'duration', line_width=2, color=color, legend_label=mode.capitalize(), source=data_sources[mode])

p1.add_tools(HoverTool(tooltips=[
    ("Distance", "@distance"),
    ("Cost (£/km)", "@cost"),
    ("Travel Mode", "@travel_mode")
]))

p2.add_tools(HoverTool(tooltips=[
    ("Distance", "@distance"),
    ("Duration (min/km)", "@duration"),
    ("Travel Mode", "@travel_mode")
]))
output_file("average_cost_per_kilometer.html")

show(p1)
output_file("average_dur_per_kilometer.html")

show(p2)

```



<div id="dae20178-90be-4522-86fe-86ff785753b3" data-root-id="p3290" style="display: contents;"></div>







<div id="cfa4bf96-8a08-475f-a970-672d8b97d8f6" data-root-id="p3323" style="display: contents;"></div>






```python

```
the code for the first interactive plot:
```python
df_drive = df[df['travel_mode'] == 'drive']
df_otherways = df[(df['travel_mode'] == 'walk') | (df['travel_mode'] == 'pt') | (df['travel_mode'] == 'cycle')]
correlation_matrix_drive = df_drive[['efficiency_score', 'environment_score']].corr()
correlation_matrix_otherways = df_otherways[['efficiency_score', 'environment_score']].corr()
sns.heatmap(correlation_matrix_drive, annot=True)
plt.show()
import pandas as pd
import plotly.graph_objects as go

# Assuming df_drive and df_otherways are your DataFrames for driving and other modes respectively.

# Calculate the value counts for fare types
drive_fare_counts = df_drive['faretype'].value_counts().reset_index()
drive_fare_counts.columns = ['Category', 'Frequency']
drive_fare_counts['Mode'] = 'Driving'
drive_fare_counts['Type'] = 'FareType'

other_fare_counts = df_otherways['faretype'].value_counts().reset_index()
other_fare_counts.columns = ['Category', 'Frequency']
other_fare_counts['Mode'] = 'Other Modes'
other_fare_counts['Type'] = 'FareType'

# Calculate the value counts for travel purposes
drive_purpose_counts = df_drive['purpose'].value_counts().reset_index()
drive_purpose_counts.columns = ['Category', 'Frequency']
drive_purpose_counts['Mode'] = 'Driving'
drive_purpose_counts['Type'] = 'Purpose'

other_purpose_counts = df_otherways['purpose'].value_counts().reset_index()
other_purpose_counts.columns = ['Category', 'Frequency']
other_purpose_counts['Mode'] = 'Other Modes'
other_purpose_counts['Type'] = 'Purpose'

# Third dataset: day of week
drive_day_counts = df_drive['day_of_week'].value_counts().reset_index()
drive_day_counts.columns = ['Category', 'Frequency']
drive_day_counts['Mode'] = 'Driving'
drive_day_counts['Type'] = 'DayOfWeek'

other_modes_day_counts = df_otherways['day_of_week'].value_counts().reset_index()
other_modes_day_counts.columns = ['Category', 'Frequency']
other_modes_day_counts['Mode'] = 'Other Modes'
other_modes_day_counts['Type'] = 'DayOfWeek'



# Combine all the data
combined_data = pd.concat([drive_fare_counts, other_fare_counts, drive_purpose_counts, other_purpose_counts, drive_day_counts, other_modes_day_counts])
# Create the interactive plot with dropdowns
fig = go.Figure()

# Add traces for each type and mode
for t in combined_data['Type'].unique():
    for m in combined_data['Mode'].unique():
        subset = combined_data[(combined_data['Type'] == t) & (combined_data['Mode'] == m)]
        fig.add_trace(go.Bar(x=subset['Category'], y=subset['Frequency'], name=f'{m}', visible=(t=='FareType')))

# Update layout with dropdowns
fig.update_layout(
    updatemenus=[
        {
            'buttons': [
                {
                    'method': 'update',
                    'label': 'Fare Type',
                    'args': [{'visible': [True, True, False, False, False, False]}, {'title': 'Travel Fare Type by Mode of Transportation'}],
                },
                {
                    'method': 'update',
                    'label': 'Purpose',
                    'args': [{'visible': [False, False, True, True, False, False]}, {'title': 'Travel Purpose by Mode of Transportation'}],
                },
                {
                    'method': 'update',
                    'label': 'Day of Week',
                    'args': [{'visible': [False, False, False, False, True, True]}, {'title': 'Travel Day of Week by Mode of Transportation'}],
                },
             
            ],
            'direction': 'down',
            'showactive': True,
        }
    ],
    title="Travel Fare Type by Mode of Transportation",
    barmode='group',
)

# Save the plot as HTML and open it in the browser
fig.show()
#fig.write_html('C:/all files/interactive_plot.gif', auto_open=False)
```
