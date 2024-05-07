<link rel="stylesheet" href="/assets/custom.css">

<h2>Final Project</h2>
<h3>Environmental Impact of Commuting in London</h3>
We've analyzed a dataset containing the different commuter trips people in London take to work.

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

This third plot is a histogram showing the counts of trips within an amount of CO2 emissions. We can see on the plot that most of the trips are in the "lower" end of the emission spectrum. However the highest emission in this bin is still 675 kg/km. 
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






Max's Notebook:

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

    



```python
purpose_counts = df["purpose"].value_counts()
purpose_counts.plot(kind="bar")
plt.show()
```


    
![png](Project%20Assignment%201_files/Project%20Assignment%201_16_0.png)
    



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



