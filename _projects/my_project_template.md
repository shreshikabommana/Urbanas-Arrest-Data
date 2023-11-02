---
name: Vegalite, Altair
tools: [Python, HTML, vega-lite]
image: assets/pngs/viz.png
description: Inventory dataset example!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Example including vega-lite


<vegachart schema-url="{{ site.baseurl }}/assets/json/cars.json" style="width: 100%"></vegachart>

# From a dictionary in Altair-Python

### Plot 1
Javascript I used from the previous assignment:
```
var vis_transform_agency = {
  // 1. data
"data": {"url": "https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv"},
  "mark": "bar",
  "encoding": {
    "x": { "field": "Agency Name", "type": "nominal"},
    "y": {"aggregate": "count"}
  }
  
};

var v = vegaEmbed('#vis3',vis_transform_agency);
```
Python Script used to create this plot:
```
chart1 = alt.Chart.from_dict({
    "data": {"url": "https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv"},
    "mark": "bar",
    "encoding": {
        "x": {"field": "Agency Name", "type": "nominal", "title": "Agency Name"},
        "y": {"aggregate": "count", "title": "Count"},
        "color": {"field": "Agency Name", "type": "nominal", "scale": {"scheme": "purples"}, "legend": None},
        "tooltip": [
            {"field": "Agency Name", "type": "nominal", "title": "Agency Name"},
            {"aggregate": "count", "title": "Count"}
        ],
    },
    "title": "Number of Buildings by Agency"
}).properties(width=600, height=400)

```

#### Changes: 
From vegalite to altair, I changed the json format to dictionary format. A few syntax changes like comment-notation changes from //-># (Java to Python) since Vegalite uses Javascript and Altair works on Python

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1.json" style="width: 100%"></vegachart>

#### Visualization Description:
In this plot, I am visualizing the number of buildings by agency using a bar chart. The x-axis represents different agency names, and the y-axis represents the count of buildings for each agency. I have chosen to color the bars by the agency name to add a visual distinction between different agencies.

#### Design Choices:
Encoding- 
- **X-axis (`"Agency Name"`):** Nominal encoding representing different agencies.
- **Y-axis (`"Count"`):** Aggregate count representing the number of buildings for each agency.
- **Color (`"Agency Name"`):** Nominal encoding for color, using the "purples" color scheme. Each agency is assigned a different shade of purple for visual separation.

#### Color Scheme Choice:
I chose the "purples" color scheme to emphasize the count of buildings for each agency. The varying shades of purple make it visually appealing and allow for easy differentiation between agencies.

#### Data Transformations:
Data Aggregation - I used Altair's aggregate function to count the number of buildings for each agency. This aggregation is reflected in the y-axis, where the count is visualized.

### PLot 2
<vegachart schema-url="{{ site.baseurl }}/assets/json/chart212.json" style="width: 100%"></vegachart>

#### Visualization Description:

In this plot, I am visualizing the relationship between the year a building was acquired and its square footage using a scatter plot. Each point represents a building, where the x-axis denotes the acquisition year, the y-axis represents the square footage, and the color distinguishes different agencies. Additionally, tooltips provide detailed information about each building.

#### Design Choices:

  - **X-axis (`"Year Acquired"`):** Temporal encoding representing the year the building was acquired.
  - **Y-axis (`"Square Footage"`):** Quantitative encoding for square footage, showing the size of each building.
  - **Color (`"Agency Name"`):** Nominal encoding for color, using the "category10" color scheme. Different agencies are assigned distinct colors for easy identification.
  - **Tooltip:**
    - Additional information about each building, including its name, year constructed, and congressional district, is displayed through tooltips.

#### Data Transformations:
  - Unlike the bar chart, no aggregation is performed here. Each point in the scatter plot represents an individual building.

#### Changes
From vegalite to altair, I changed the json format to dictionary format. A few syntax changes like comment-notation changes from //-># (Java to Python) since Vegalite uses Javascript and Altair works on Python

### Plot 3
# Static Side by Side Dashboard

<vegachart schema-url="{{ site.baseurl }}/assets/json/first_dashboard.json" style="width: 100%"></vegachart>

Certainly, let's focus on the description for the combined chart:

### Combined Chart (Scatter Plot and Bar Chart):

#### Composition:
  - The chart is a combination of a scatter plot and a bar chart presented side by side.
  - Both charts share the same height (300).
#### Scatter Plot - Left Side:
#### Encoding Types:
  - X-axis (`"Year Acquired"`): Temporal encoding representing the year the building was acquired.
  - Y-axis (`"Square Footage"`): Quantitative encoding for square footage, showing the size of each building.
  - Color (`"Agency Name"`): Nominal encoding for color, using the "category10" color scheme.
  - Tooltip: Additional information about each building.
#### Design Choices:
  - Mark type: Circle, filled, size = 100.
  - Visualizing the relationship between acquisition year and square footage, with color distinguishing different agencies.
#### Data Transformations:
  - No aggregation; each point represents an individual building.
#### Bar Chart - Right Side:
#### Encoding Types:
  - X-axis (`"Total Floors"`): Quantitative encoding representing the total number of floors in a building.
  - Y-axis (`"Count"`): Aggregate count representing the number of buildings for each total floors value.
  - Color (`"Agency Name"`): Nominal encoding for color, using the "category10" color scheme.
  - Tooltip: Additional information about the total floors, agency name, and count of buildings.
#### Design Choices:
  - Mark type: Bar.
  - Visualizing the distribution of buildings based on the total number of floors, with color distinguishing different agencies.
#### Data Transformations:
  - Aggregation is applied to count the number of buildings for each total floors value.
#### Interactivity:
  - The current design does not include interactive elements.

### Plot 4
# Interactive Side by Side Dashboard

<vegachart schema-url="{{ site.baseurl }}/assets/json/interactive_plot.json" style="width: 100%"></vegachart>

This dashboard is same as the previous dashboard, with the addition of a brush selection for interactivity.

Interactivity:
The bar chart is filtered based on the brush selection in the scatter plot. This interactive feature allows users to observe the distribution of buildings by total floors within the selected region.

Interactivity Overview:
The brush selection on the scatter plot facilitates a dynamic exploration of specific data points, and the bar chart is updated accordingly based on the selected region.


# ONLY Altair section

### Plot 5
<vegachart schema-url="{{ site.baseurl }}/assets/json/altair_plot.json" style="width: 100%"></vegachart>

This Altair chart is same as Plot 2.
The syntax directly uses Altair's functions and attributes, eschewing the dictionary format.
The mark_point() function is employed to specify the point mark for the scatter plot.
Encoding is achieved using the encode method, where the x-axis represents the acquisition year ('Year Acquired:T'), the y-axis depicts square footage ('Square Footage:Q'), and the color distinguishes different agencies (alt.Color('Agency Name:N', scale=alt.Scale(scheme='viridis'))).

Encoding details in altair :
N- nominal data encoding
O- oridinal data encoding
T- temporal data encoding
Q- quantitative data encoding

### Plot 6- How many buildings in each county?

<vegachart schema-url="{{ site.baseurl }}/assets/json/alt3.json" style="width: 100%"></vegachart>

#### Description:
The visualization depicts a bar chart illustrating the distribution of counts for each county in the dataset.
Design Choices:

#### Encoding Types:
**X-axis ("County:N"):** Nominal encoding representing the different counties.
**Y-axis ("Count:Q"):** Quantitative encoding representing the count of occurrences for each county.
**Color Scheme:**The bars are colored green (color='green'), chosen for visual distinction and aesthetic appeal.

#### Data Transformations:
A new DataFrame (count_df) is created through Pandas, aggregating counts of unique values in the "County" column.
The x-axis is sorted based on count values in descending order (sort='-y'), enhancing the clarity of the visualization.

#### Comparison to Homework #7:
In Homework 7, I just created this plot using matplotlib, here I made the transformations and visualizations in Altair.

### Plot 7- Interactive Dashboards with Altair: 

These dashboards are same as the interactive dasboards I created in the Dasboards section (Plot 4)
These use altair.Chart() method instead of altair.Chart.from_dict() method.
The Design choices and the description are the same as the previous dashboards. I tried different markers for the same graph to check how interactivity and the visuals differ.

Code:
```
brush = alt.selection_interval(encodings=['x','y'])

altair_chart1 = alt.Chart(data_url).mark_point().encode(
    x='Year Acquired:T',
    y='Square Footage:Q',
    color = alt.Color('Agency Name:N',scale=alt.Scale(scheme='viridis'))).add_selection(brush)
alt2 = alt.Chart(data_url).mark_bar().encode(
    alt.X("Total Floors:Q"),
    alt.Y("count()"),
    alt.Color("Agency Name:N",scale=alt.Scale(scheme='pastel1'))
).properties(height=300).transform_filter(brush)    

db2 = altair_chart1 | alt2
```

### Rectangular Plot and bar chart 
<vegachart schema-url="{{ site.baseurl }}/assets/json/dynamicdb1.json" style="width: 100%"></vegachart>

### Scatter Plot and bar chart 
<vegachart schema-url="{{ site.baseurl }}/assets/json/dynamicdb2.json" style="width: 100%"></vegachart>

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/sanjnaapai/sanjnaapai.github.io/blob/main/python_notebooks/Homework%238Link.ipynb" text="The Analysis" %}
</div>

