
---
title: "Creating Choropleth Maps With Python"
author: "Osman Cakir"
date: 2019-03-09
description: "Choropleth Maps with Python and Plotly packages."
type: technical_note
draft: false
---
___
# Choropleth Maps

Here we are going to create a US map with agricultural production data on it. This little project was from my master's degree in economics but I am excited to create a map with art history too. If you have any idea and (data) just reach me up and we can make it!. 

This code below creates an interactive map plot with plotly. Unfortunately you will be able to see the maps if you run and try the code yourself due to plotly being javascript based. But go ahead and try and let me know. 

## Offline Plotly Usage

Get imports and set everything up to be working offline.


```python
import plotly.plotly as py
import plotly.graph_objs as go 
from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot
```

Now set up everything so that the figures show up in the notebook:


```python
init_notebook_mode(connected=True) 
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>


More info on other options for Offline Plotly usage can be found [here](https://plot.ly/python/offline/).

## Choropleth US Maps

Plotly's mapping can be a bit hard to get used to at first, remember to reference the cheat sheet in the data visualization folder, or [find it online here](https://images.plot.ly/plotly-documentation/images/python_cheat_sheet.pdf).


```python
import pandas as pd
```

Now we need to begin to build our data dictionary. Easiest way to do this is to use the **dict()** function of the general form:

* type = 'choropleth',
* locations = list of states
* locationmode = 'USA-states'
* colorscale= 

Either a predefined string:

    'pairs' | 'Greys' | 'Greens' | 'Bluered' | 'Hot' | 'Picnic' | 'Portland' | 'Jet' | 'RdBu' | 'Blackbody' | 'Earth' | 'Electric' | 'YIOrRd' | 'YIGnBu'

or create a [custom colorscale](https://plot.ly/python/heatmap-and-contour-colorscales/)

* text= list or array of text to display per point
* z= array of values on z axis (color of state)
* colorbar = {'title':'Colorbar Title'})

Here is a simple example:


```python
data = dict(type = 'choropleth',
            locations = ['AZ','CA','NY'],
            locationmode = 'USA-states',
            colorscale= 'Portland',
            text= ['text1','text2','text3'],
            z=[1.0,2.0,3.0],
            colorbar = {'title':'Colorbar Title'})
```

Then we create the layout nested dictionary:


```python
layout = dict(geo = {'scope':'usa'})
```

Then we use: 

    go.Figure(data = [data],layout = layout)
    
to set up the object that finally gets passed into iplot()


```python
choromap = go.Figure(data = [data],layout = layout)
```


```python
iplot(choromap)
```


<div id="38e6ece1-3a06-4c11-b1d9-9556eb6a0eab" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("38e6ece1-3a06-4c11-b1d9-9556eb6a0eab", [{"z": [1.0, 2.0, 3.0], "locationmode": "USA-states", "text": ["text1", "text2", "text3"], "locations": ["AZ", "CA", "NY"], "colorscale": "Portland", "type": "choropleth", "colorbar": {"title": "Colorbar Title"}}], {"geo": {"scope": "usa"}}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>




## Real Data US Map Choropleth

Now let's show an example with some real data as well as some other options we can add to the dictionaries in data and layout.


```python
df = pd.read_csv('2011_US_AGRI_Exports')
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>code</th>
      <th>state</th>
      <th>category</th>
      <th>total exports</th>
      <th>beef</th>
      <th>pork</th>
      <th>poultry</th>
      <th>dairy</th>
      <th>fruits fresh</th>
      <th>fruits proc</th>
      <th>total fruits</th>
      <th>veggies fresh</th>
      <th>veggies proc</th>
      <th>total veggies</th>
      <th>corn</th>
      <th>wheat</th>
      <th>cotton</th>
      <th>text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AL</td>
      <td>Alabama</td>
      <td>state</td>
      <td>1390.63</td>
      <td>34.4</td>
      <td>10.6</td>
      <td>481.0</td>
      <td>4.06</td>
      <td>8.0</td>
      <td>17.1</td>
      <td>25.11</td>
      <td>5.5</td>
      <td>8.9</td>
      <td>14.33</td>
      <td>34.9</td>
      <td>70.0</td>
      <td>317.61</td>
      <td>Alabama&lt;br&gt;Beef 34.4 Dairy 4.06&lt;br&gt;Fruits 25.1...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AK</td>
      <td>Alaska</td>
      <td>state</td>
      <td>13.31</td>
      <td>0.2</td>
      <td>0.1</td>
      <td>0.0</td>
      <td>0.19</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.6</td>
      <td>1.0</td>
      <td>1.56</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>Alaska&lt;br&gt;Beef 0.2 Dairy 0.19&lt;br&gt;Fruits 0.0 Ve...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AZ</td>
      <td>Arizona</td>
      <td>state</td>
      <td>1463.17</td>
      <td>71.3</td>
      <td>17.9</td>
      <td>0.0</td>
      <td>105.48</td>
      <td>19.3</td>
      <td>41.0</td>
      <td>60.27</td>
      <td>147.5</td>
      <td>239.4</td>
      <td>386.91</td>
      <td>7.3</td>
      <td>48.7</td>
      <td>423.95</td>
      <td>Arizona&lt;br&gt;Beef 71.3 Dairy 105.48&lt;br&gt;Fruits 60...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AR</td>
      <td>Arkansas</td>
      <td>state</td>
      <td>3586.02</td>
      <td>53.2</td>
      <td>29.4</td>
      <td>562.9</td>
      <td>3.53</td>
      <td>2.2</td>
      <td>4.7</td>
      <td>6.88</td>
      <td>4.4</td>
      <td>7.1</td>
      <td>11.45</td>
      <td>69.5</td>
      <td>114.5</td>
      <td>665.44</td>
      <td>Arkansas&lt;br&gt;Beef 53.2 Dairy 3.53&lt;br&gt;Fruits 6.8...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>CA</td>
      <td>California</td>
      <td>state</td>
      <td>16472.88</td>
      <td>228.7</td>
      <td>11.1</td>
      <td>225.4</td>
      <td>929.95</td>
      <td>2791.8</td>
      <td>5944.6</td>
      <td>8736.40</td>
      <td>803.2</td>
      <td>1303.5</td>
      <td>2106.79</td>
      <td>34.6</td>
      <td>249.3</td>
      <td>1064.95</td>
      <td>California&lt;br&gt;Beef 228.7 Dairy 929.95&lt;br&gt;Frui...</td>
    </tr>
  </tbody>
</table>
</div>



Now out data dictionary with some extra marker and colorbar arguments:


```python
data = dict(type='choropleth',
            colorscale = 'YIOrRd',
            locations = df['code'],
            z = df['total exports'],
            locationmode = 'USA-states',
            text = df['text'],
            marker = dict(line = dict(color = 'rgb(255,255,255)',width = 2)),
            colorbar = {'title':"Millions USD"}
            ) 
```

And our layout dictionary with some more arguments:


```python
layout = dict(title = '2011 US Agriculture Exports by State',
              geo = dict(scope='usa',
                         showlakes = True,
                         lakecolor = 'rgb(85,173,240)')
             )
```


```python
choromap = go.Figure(data = [data],layout = layout)
```


```python
iplot(choromap)
```


<div id="0a0f7352-abd4-4bb8-840b-5901e1681008" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("0a0f7352-abd4-4bb8-840b-5901e1681008", [{"z": [1390.63, 13.31, 1463.17, 3586.02, 16472.88, 1851.33, 259.62, 282.19, 3764.09, 2860.84, 401.84, 2078.89, 8709.48, 5050.23, 11273.76, 4589.01, 1889.15, 1914.23, 278.37, 692.75, 248.65, 3164.16, 7192.33, 2170.8, 3933.42, 1718.0, 7114.13, 139.89, 73.06, 500.4, 751.58, 1488.9, 3806.05, 3761.96, 3979.79, 1646.41, 1794.57, 1969.87, 31.59, 929.93, 3770.19, 1535.13, 6648.22, 453.39, 180.14, 1146.48, 3894.81, 138.89, 3090.23, 349.69], "locationmode": "USA-states", "text": ["Alabama<br>Beef 34.4 Dairy 4.06<br>Fruits 25.11 Veggies 14.33<br>Wheat 70.0 Corn 34.9", "Alaska<br>Beef 0.2 Dairy 0.19<br>Fruits 0.0 Veggies 1.56<br>Wheat 0.0 Corn 0.0", "Arizona<br>Beef 71.3 Dairy 105.48<br>Fruits 60.27 Veggies 386.91<br>Wheat 48.7 Corn 7.3", "Arkansas<br>Beef 53.2 Dairy 3.53<br>Fruits 6.88 Veggies 11.45<br>Wheat 114.5 Corn 69.5", " California<br>Beef 228.7 Dairy 929.95<br>Fruits 8736.4 Veggies 2106.79<br>Wheat 249.3 Corn 34.6", "Colorado<br>Beef 261.4 Dairy 71.94<br>Fruits 17.99 Veggies 118.27<br>Wheat 400.5 Corn 183.2", "Connecticut<br>Beef 1.1 Dairy 9.49<br>Fruits 13.1 Veggies 11.16<br>Wheat 0.0 Corn 0.0", "Delaware<br>Beef 0.4 Dairy 2.3<br>Fruits 1.53 Veggies 20.03<br>Wheat 22.9 Corn 26.9", "Florida<br>Beef 42.6 Dairy 66.31<br>Fruits 1371.36 Veggies 450.86<br>Wheat 1.8 Corn 3.5", "Georgia<br>Beef 31.0 Dairy 38.38<br>Fruits 233.51 Veggies 154.77<br>Wheat 65.4 Corn 57.8", "Hawaii<br>Beef 4.0 Dairy 1.16<br>Fruits 55.51 Veggies 24.83<br>Wheat 0.0 Corn 0.0", "Idaho<br>Beef 119.8 Dairy 294.6<br>Fruits 21.64 Veggies 319.19<br>Wheat 568.2 Corn 24.0", "Illinois<br>Beef 53.7 Dairy 45.82<br>Fruits 12.53 Veggies 39.95<br>Wheat 223.8 Corn 2228.5", "Indiana<br>Beef 21.9 Dairy 89.7<br>Fruits 12.98 Veggies 37.89<br>Wheat 114.0 Corn 1123.2", "Iowa<br>Beef 289.8 Dairy 107.0<br>Fruits 3.24 Veggies 7.1<br>Wheat 3.1 Corn 2529.8", "Kansas<br>Beef 659.3 Dairy 65.45<br>Fruits 3.11 Veggies 9.32<br>Wheat 1426.5 Corn 457.3", "Kentucky<br>Beef 54.8 Dairy 28.27<br>Fruits 6.6 Veggies 0.0<br>Wheat 149.3 Corn 179.1", "Louisiana<br>Beef 19.8 Dairy 6.02<br>Fruits 17.83 Veggies 17.25<br>Wheat 78.7 Corn 91.4", "Maine<br>Beef 1.4 Dairy 16.18<br>Fruits 52.01 Veggies 62.9<br>Wheat 0.0 Corn 0.0", "Maryland<br>Beef 5.6 Dairy 24.81<br>Fruits 12.9 Veggies 20.43<br>Wheat 55.8 Corn 54.1", "Massachusetts<br>Beef 0.6 Dairy 5.81<br>Fruits 80.83 Veggies 21.13<br>Wheat 0.0 Corn 0.0", "Michigan<br>Beef 37.7 Dairy 214.82<br>Fruits 257.69 Veggies 189.96<br>Wheat 247.0 Corn 381.5", "Minnesota<br>Beef 112.3 Dairy 218.05<br>Fruits 7.91 Veggies 120.37<br>Wheat 538.1 Corn 1264.3", "Mississippi<br>Beef 12.8 Dairy 5.45<br>Fruits 17.04 Veggies 27.87<br>Wheat 102.2 Corn 110.0", "Missouri<br>Beef 137.2 Dairy 34.26<br>Fruits 13.18 Veggies 17.9<br>Wheat 161.7 Corn 428.8", "Montana<br>Beef 105.0 Dairy 6.82<br>Fruits 3.3 Veggies 45.27<br>Wheat 1198.1 Corn 5.4", "Nebraska<br>Beef 762.2 Dairy 30.07<br>Fruits 2.16 Veggies 53.5<br>Wheat 292.3 Corn 1735.9", "Nevada<br>Beef 21.8 Dairy 16.57<br>Fruits 1.19 Veggies 27.93<br>Wheat 5.4 Corn 0.0", "New Hampshire<br>Beef 0.6 Dairy 7.46<br>Fruits 7.98 Veggies 4.5<br>Wheat 0.0 Corn 0.0", "New Jersey<br>Beef 0.8 Dairy 3.37<br>Fruits 109.45 Veggies 56.54<br>Wheat 6.7 Corn 10.1", "New Mexico<br>Beef 117.2 Dairy 191.01<br>Fruits 101.9 Veggies 43.88<br>Wheat 13.9 Corn 11.2", "New York<br>Beef 22.2 Dairy 331.8<br>Fruits 202.56 Veggies 143.37<br>Wheat 29.9 Corn 106.1", "North Carolina<br>Beef 24.8 Dairy 24.9<br>Fruits 74.47 Veggies 150.45<br>Wheat 200.3 Corn 92.2", "North Dakota<br>Beef 78.5 Dairy 8.14<br>Fruits 0.25 Veggies 130.79<br>Wheat 1664.5 Corn 236.1", "Ohio<br>Beef 36.2 Dairy 134.57<br>Fruits 27.21 Veggies 53.53<br>Wheat 207.4 Corn 535.1", "Oklahoma<br>Beef 337.6 Dairy 24.35<br>Fruits 9.24 Veggies 8.9<br>Wheat 324.8 Corn 27.5", "Oregon<br>Beef 58.8 Dairy 63.66<br>Fruits 315.04 Veggies 126.5<br>Wheat 320.3 Corn 11.7", "Pennsylvania<br>Beef 50.9 Dairy 280.87<br>Fruits 89.48 Veggies 38.26<br>Wheat 41.0 Corn 112.1", "Rhode Island<br>Beef 0.1 Dairy 0.52<br>Fruits 2.83 Veggies 3.02<br>Wheat 0.0 Corn 0.0", "South Carolina<br>Beef 15.2 Dairy 7.62<br>Fruits 53.45 Veggies 42.66<br>Wheat 55.3 Corn 32.1", "South Dakota<br>Beef 193.5 Dairy 46.77<br>Fruits 0.8 Veggies 4.06<br>Wheat 704.5 Corn 643.6", "Tennessee<br>Beef 51.1 Dairy 21.18<br>Fruits 6.23 Veggies 24.67<br>Wheat 100.0 Corn 88.8", "Texas<br>Beef 961.0 Dairy 240.55<br>Fruits 99.9 Veggies 115.23<br>Wheat 309.7 Corn 167.2", "Utah<br>Beef 27.9 Dairy 48.6<br>Fruits 12.34 Veggies 6.6<br>Wheat 42.8 Corn 5.3", "Vermont<br>Beef 6.2 Dairy 65.98<br>Fruits 8.01 Veggies 4.05<br>Wheat 0.0 Corn 0.0", "Virginia<br>Beef 39.5 Dairy 47.85<br>Fruits 36.48 Veggies 27.25<br>Wheat 77.5 Corn 39.5", "Washington<br>Beef 59.2 Dairy 154.18<br>Fruits 1738.57 Veggies 363.79<br>Wheat 786.3 Corn 29.5", "West Virginia<br>Beef 12.0 Dairy 3.9<br>Fruits 11.54 Veggies 0.0<br>Wheat 1.6 Corn 3.5", "Wisconsin<br>Beef 107.3 Dairy 633.6<br>Fruits 133.8 Veggies 148.99<br>Wheat 96.7 Corn 460.5", "Wyoming<br>Beef 75.1 Dairy 2.89<br>Fruits 0.17 Veggies 10.23<br>Wheat 20.7 Corn 9.0"], "marker": {"line": {"color": "rgb(255,255,255)", "width": 2}}, "locations": ["AL", "AK", "AZ", "AR", "CA", "CO", "CT", "DE", "FL", "GA", "HI", "ID", "IL", "IN", "IA", "KS", "KY", "LA", "ME", "MD", "MA", "MI", "MN", "MS", "MO", "MT", "NE", "NV", "NH", "NJ", "NM", "NY", "NC", "ND", "OH", "OK", "OR", "PA", "RI", "SC", "SD", "TN", "TX", "UT", "VT", "VA", "WA", "WV", "WI", "WY"], "colorscale": "YIOrRd", "type": "choropleth", "colorbar": {"title": "Millions USD"}}], {"geo": {"lakecolor": "rgb(85,173,240)", "showlakes": true, "scope": "usa"}, "title": "2011 US Agriculture Exports by State"}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


# World Choropleth Map

Now let's see an example with a World Map:


```python
df = pd.read_csv('2014_World_GDP')
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>COUNTRY</th>
      <th>GDP (BILLIONS)</th>
      <th>CODE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>21.71</td>
      <td>AFG</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>13.40</td>
      <td>ALB</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>227.80</td>
      <td>DZA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>American Samoa</td>
      <td>0.75</td>
      <td>ASM</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Andorra</td>
      <td>4.80</td>
      <td>AND</td>
    </tr>
  </tbody>
</table>
</div>




```python
data = dict(
        type = 'choropleth',
        locations = df['CODE'],
        z = df['GDP (BILLIONS)'],
        text = df['COUNTRY'],
        colorbar = {'title' : 'GDP Billions US'},
      ) 
```


```python
layout = dict(
    title = '2014 Global GDP',
    geo = dict(
        showframe = False,
        projection = {'type':'Mercator'}
    )
)
```


```python
choromap = go.Figure(data = [data],layout = layout)
iplot(choromap)
```


<div id="62a24a2c-9495-41df-a261-80a15e6aba96" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("62a24a2c-9495-41df-a261-80a15e6aba96", [{"text": ["Afghanistan", "Albania", "Algeria", "American Samoa", "Andorra", "Angola", "Anguilla", "Antigua and Barbuda", "Argentina", "Armenia", "Aruba", "Australia", "Austria", "Azerbaijan", "Bahamas, The", "Bahrain", "Bangladesh", "Barbados", "Belarus", "Belgium", "Belize", "Benin", "Bermuda", "Bhutan", "Bolivia", "Bosnia and Herzegovina", "Botswana", "Brazil", "British Virgin Islands", "Brunei", "Bulgaria", "Burkina Faso", "Burma", "Burundi", "Cabo Verde", "Cambodia", "Cameroon", "Canada", "Cayman Islands", "Central African Republic", "Chad", "Chile", "China", "Colombia", "Comoros", "Congo, Democratic Republic of the", "Congo, Republic of the", "Cook Islands", "Costa Rica", "Cote d'Ivoire", "Croatia", "Cuba", "Curacao", "Cyprus", "Czech Republic", "Denmark", "Djibouti", "Dominica", "Dominican Republic", "Ecuador", "Egypt", "El Salvador", "Equatorial Guinea", "Eritrea", "Estonia", "Ethiopia", "Falkland Islands (Islas Malvinas)", "Faroe Islands", "Fiji", "Finland", "France", "French Polynesia", "Gabon", "Gambia, The", "Georgia", "Germany", "Ghana", "Gibraltar", "Greece", "Greenland", "Grenada", "Guam", "Guatemala", "Guernsey", "Guinea-Bissau", "Guinea", "Guyana", "Haiti", "Honduras", "Hong Kong", "Hungary", "Iceland", "India", "Indonesia", "Iran", "Iraq", "Ireland", "Isle of Man", "Israel", "Italy", "Jamaica", "Japan", "Jersey", "Jordan", "Kazakhstan", "Kenya", "Kiribati", "Korea, North", "Korea, South", "Kosovo", "Kuwait", "Kyrgyzstan", "Laos", "Latvia", "Lebanon", "Lesotho", "Liberia", "Libya", "Liechtenstein", "Lithuania", "Luxembourg", "Macau", "Macedonia", "Madagascar", "Malawi", "Malaysia", "Maldives", "Mali", "Malta", "Marshall Islands", "Mauritania", "Mauritius", "Mexico", "Micronesia, Federated States of", "Moldova", "Monaco", "Mongolia", "Montenegro", "Morocco", "Mozambique", "Namibia", "Nepal", "Netherlands", "New Caledonia", "New Zealand", "Nicaragua", "Nigeria", "Niger", "Niue", "Northern Mariana Islands", "Norway", "Oman", "Pakistan", "Palau", "Panama", "Papua New Guinea", "Paraguay", "Peru", "Philippines", "Poland", "Portugal", "Puerto Rico", "Qatar", "Romania", "Russia", "Rwanda", "Saint Kitts and Nevis", "Saint Lucia", "Saint Martin", "Saint Pierre and Miquelon", "Saint Vincent and the Grenadines", "Samoa", "San Marino", "Sao Tome and Principe", "Saudi Arabia", "Senegal", "Serbia", "Seychelles", "Sierra Leone", "Singapore", "Sint Maarten", "Slovakia", "Slovenia", "Solomon Islands", "Somalia", "South Africa", "South Sudan", "Spain", "Sri Lanka", "Sudan", "Suriname", "Swaziland", "Sweden", "Switzerland", "Syria", "Taiwan", "Tajikistan", "Tanzania", "Thailand", "Timor-Leste", "Togo", "Tonga", "Trinidad and Tobago", "Tunisia", "Turkey", "Turkmenistan", "Tuvalu", "Uganda", "Ukraine", "United Arab Emirates", "United Kingdom", "United States", "Uruguay", "Uzbekistan", "Vanuatu", "Venezuela", "Vietnam", "Virgin Islands", "West Bank", "Yemen", "Zambia", "Zimbabwe"], "z": [21.71, 13.4, 227.8, 0.75, 4.8, 131.4, 0.18, 1.24, 536.2, 10.88, 2.52, 1483.0, 436.1, 77.91, 8.65, 34.05, 186.6, 4.28, 75.25, 527.8, 1.67, 9.24, 5.2, 2.09, 34.08, 19.55, 16.3, 2244.0, 1.1, 17.43, 55.08, 13.38, 65.29, 3.04, 1.98, 16.9, 32.16, 1794.0, 2.25, 1.73, 15.84, 264.1, 10360.0, 400.1, 0.72, 32.67, 14.11, 0.18, 50.46, 33.96, 57.18, 77.15, 5.6, 21.34, 205.6, 347.2, 1.58, 0.51, 64.05, 100.5, 284.9, 25.14, 15.4, 3.87, 26.36, 49.86, 0.16, 2.32, 4.17, 276.3, 2902.0, 7.15, 20.68, 0.92, 16.13, 3820.0, 35.48, 1.85, 246.4, 2.16, 0.84, 4.6, 58.3, 2.74, 1.04, 6.77, 3.14, 8.92, 19.37, 292.7, 129.7, 16.2, 2048.0, 856.1, 402.7, 232.2, 245.8, 4.08, 305.0, 2129.0, 13.92, 4770.0, 5.77, 36.55, 225.6, 62.72, 0.16, 28.0, 1410.0, 5.99, 179.3, 7.65, 11.71, 32.82, 47.5, 2.46, 2.07, 49.34, 5.11, 48.72, 63.93, 51.68, 10.92, 11.19, 4.41, 336.9, 2.41, 12.04, 10.57, 0.18, 4.29, 12.72, 1296.0, 0.34, 7.74, 6.06, 11.73, 4.66, 112.6, 16.59, 13.11, 19.64, 880.4, 11.1, 201.0, 11.85, 594.3, 8.29, 0.01, 1.23, 511.6, 80.54, 237.5, 0.65, 44.69, 16.1, 31.3, 208.2, 284.6, 552.2, 228.2, 93.52, 212.0, 199.0, 2057.0, 8.0, 0.81, 1.35, 0.56, 0.22, 0.75, 0.83, 1.86, 0.36, 777.9, 15.88, 42.65, 1.47, 5.41, 307.9, 304.1, 99.75, 49.93, 1.16, 2.37, 341.2, 11.89, 1400.0, 71.57, 70.03, 5.27, 3.84, 559.1, 679.0, 64.7, 529.5, 9.16, 36.62, 373.8, 4.51, 4.84, 0.49, 29.63, 49.12, 813.3, 43.5, 0.04, 26.09, 134.9, 416.4, 2848.0, 17420.0, 55.6, 63.08, 0.82, 209.2, 187.8, 5.08, 6.64, 45.45, 25.61, 13.74], "type": "choropleth", "locations": ["AFG", "ALB", "DZA", "ASM", "AND", "AGO", "AIA", "ATG", "ARG", "ARM", "ABW", "AUS", "AUT", "AZE", "BHM", "BHR", "BGD", "BRB", "BLR", "BEL", "BLZ", "BEN", "BMU", "BTN", "BOL", "BIH", "BWA", "BRA", "VGB", "BRN", "BGR", "BFA", "MMR", "BDI", "CPV", "KHM", "CMR", "CAN", "CYM", "CAF", "TCD", "CHL", "CHN", "COL", "COM", "COD", "COG", "COK", "CRI", "CIV", "HRV", "CUB", "CUW", "CYP", "CZE", "DNK", "DJI", "DMA", "DOM", "ECU", "EGY", "SLV", "GNQ", "ERI", "EST", "ETH", "FLK", "FRO", "FJI", "FIN", "FRA", "PYF", "GAB", "GMB", "GEO", "DEU", "GHA", "GIB", "GRC", "GRL", "GRD", "GUM", "GTM", "GGY", "GNB", "GIN", "GUY", "HTI", "HND", "HKG", "HUN", "ISL", "IND", "IDN", "IRN", "IRQ", "IRL", "IMN", "ISR", "ITA", "JAM", "JPN", "JEY", "JOR", "KAZ", "KEN", "KIR", "KOR", "PRK", "KSV", "KWT", "KGZ", "LAO", "LVA", "LBN", "LSO", "LBR", "LBY", "LIE", "LTU", "LUX", "MAC", "MKD", "MDG", "MWI", "MYS", "MDV", "MLI", "MLT", "MHL", "MRT", "MUS", "MEX", "FSM", "MDA", "MCO", "MNG", "MNE", "MAR", "MOZ", "NAM", "NPL", "NLD", "NCL", "NZL", "NIC", "NGA", "NER", "NIU", "MNP", "NOR", "OMN", "PAK", "PLW", "PAN", "PNG", "PRY", "PER", "PHL", "POL", "PRT", "PRI", "QAT", "ROU", "RUS", "RWA", "KNA", "LCA", "MAF", "SPM", "VCT", "WSM", "SMR", "STP", "SAU", "SEN", "SRB", "SYC", "SLE", "SGP", "SXM", "SVK", "SVN", "SLB", "SOM", "ZAF", "SSD", "ESP", "LKA", "SDN", "SUR", "SWZ", "SWE", "CHE", "SYR", "TWN", "TJK", "TZA", "THA", "TLS", "TGO", "TON", "TTO", "TUN", "TUR", "TKM", "TUV", "UGA", "UKR", "ARE", "GBR", "USA", "URY", "UZB", "VUT", "VEN", "VNM", "VGB", "WBG", "YEM", "ZMB", "ZWE"], "colorbar": {"title": "GDP Billions US"}}], {"geo": {"showframe": false, "projection": {"type": "Mercator"}}, "title": "2014 Global GDP"}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


# Thank you for reading!
