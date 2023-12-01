---
name: Vegalite, Altair
tools: [Python, HTML, vega-lite]
image: assets/pngs/viz.png
description: Final Project!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
## Inside Urbana's Arrest Data: A Visual Narrative
##### Authors: Kavya Moharana, Sanjana Pai, Ridah Shaikh, Shreshika Bommana

<img src="{{ site.baseurl }}/assets/pngs/contextviz1.png" alt="Italian Trulli">
<div class="center">
<a href="https://datausa.io/profile/geo/urbana-il#race_and_ethnicity" class="button">Source- Urbana Police data</a>
</div>
<vegachart schema-url="{{ site.baseurl }}/assets/json/interactive_v2.json" style="width: 100%"></vegachart>

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2.v2.json" style="width: 100%"></vegachart>

<iframe width="720px" height="480px" src="https://datausa.io/profile/geo/urbana-il/demographics/race_and_ethnicity?viz=true" frameborder="0" ></iframe>

<div class="left">
<a href="https://datausa.io/profile/geo/urbana-il#race_and_ethnicity" class="button">Source- Urbana Police data</a>
</div>



<vegachart schema-url="{{ site.baseurl }}/assets/json/race.v2.json" style="width: 100%"></vegachart>

<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/sanjnaapai/sanjnaapai.github.io/blob/main/python_notebooks/Workbook.ipynb" text="The Analysis" %}
</div>

