---
title: "Schmankerl Time Machine"
author: "Osman Cakir"
date: 2019-07-16
description: "Codind da Vinci Süd 2019 Winner Project, text analysis, digital humanities"
type: technical_note
draft: false
---
<p style="text-align: center;">
  <img src="Schmankerl_Time_Machine_Project/empty.png" width="25%" />
  <img alt="Schmankerl Time Machine Logo" src="Schmankerl_Time_Machine_Project/logo_with_cdv.png" width="50%" />
</p>

_____

The project was created as part of the culture hackathon for open culture data, [Coding da Vinci Süd 2019](https://codingdavinci.de/events/sued/), and won the prize in the most technical category. 

## Project Description



> Always the same dishes on your dining table? Are you desperately looking for some inspiration for your culinary everyday life? So not all hope is lost yet! <br /> <br /> "Schmankerl Time Machine" invites you to a culinary time travel through the traditional history of Munich-based restaurants during the past 150 years. First get an overview of Munich's gastronomic legends. Next compose your unforgettable menu from a portfolio consisting of more than 380 menus. Recipes are already linked to them. How about a lobster cocktail, followed by a rabbit in the terrine and some venison nuts, finaly crowned by Prince Pückler's ice cream variation? Let yourself be inspired by the suggestions of other users when creating your menu. Upload the menu of your favourite Munich restaurant to expand the data collection even further.
 <br /> <br /> Let's treat!



A detailed project description can be found under [PROJECT DESCRIPTION.md] (PROJECT DESCRIPTION.md).

## Data

A *Snapshot* of the extracted data can be found in the [Data] (DATA.md) folder.

* **addresses** Adresses, annotated in tht menus.
* **categories** Category of the dishes and drinks (Appetizers, main courses etc).
* **entries** Links to the food and drinks in the menus, including price and quantities.
* **items** Description of the food and drinks.
* **menus** Metadata of the Menus. 
* **owners** Owners of the restaurants which their menus were annotated.
* **recipies** Recipes of the dishes and the drinks.
* **restaurants** Metadata about the restaurants.
* **zones** Entries about the menus and their locations (*Bounding Boxes*).

The recipes go back to [Chefkoch.de] (https://chefkoch.de/) and are available at: https://chefkoch.de/rezepte/{recipy_id}/. The glossary is based on data of German-language [Wikipedia](https://en.wikipedia.org/wiki/Bavarian_cuisine):

* **glossary_categories** Categories of food and drinks based on Wikipedia.
* **glossary_entries** Links of the food and drinks to categories based on Wikipedia.
* **glossary_items** Description of food and drinks based on Wikipedia.

## Implementation

### Jupyter Notebooks

In the [Notebooks](Notebooks/) folder there are some sample notebooks for evaluation, which show, among other things, the temporal distribution of the menus.

<p style="max-width: 850px;">
  <img alt="Speisekarten Wordcloud Schwein" src="Schmankerl_Time_Machine_Project/wordcloud_pig.png" width="57%" />
  <img alt="Speisekarten Wordcloud Bier" src="Schmankerl_Time_Machine_Project/wordcloud_beer.png" width="31%" />
</p>

### Shiny Web-Application

In the [Webanwendung](Webanwendung/) (Webapplication) folder you will find all the code for the Shiny Web application that is currently available at https://dhvlab.gwi.uni-muenchen.de/schmankerltimemachine/ Our project is hosted by the [LMU Center for Digital Humanities] (https : //www.itg.uni-muenchen.de/index.html).



<p float="left" style="max-width: 850px;">
  <img alt="Screenshot 1" src="Schmankerl_Time_Machine_Project/screenshot-1.png" width="22%" />
  <img alt="Screenshot 2" src="Schmankerl_Time_Machine_Project/screenshot-2.png" width="22%" /> 
  <img alt="Screenshot 3" src="Schmankerl_Time_Machine_Project/screenshot-3.png" width="22%" />
  <img alt="Screenshot 4" src="Schmankerl_Time_Machine_Project/screenshot-4.png" width="22%" />
  <img alt="Screenshot 5" src="Schmankerl_Time_Machine_Project/screenshot-5.png" width="22%" />
  <img alt="Screenshot 6" src="Schmankerl_Time_Machine_Project/screenshot-6.png" width="22%" /> 
  <img alt="Screenshot 7" src="Schmankerl_Time_Machine_Project/screenshot-7.png" width="22%" />
  <img alt="Screenshot 8" src="Schmankerl_Time_Machine_Project/screenshot-8.png" width="22%" />
</p>

## Scripts

### Extraction of the Data from TEI-Data

The following Python-based script is available for extracting the data from the TEI-Data exported from Transkribus (coordinates in the form of *Bounding Boxes*). It generates CSV files for each food and beverage, entries about menus, owners and addresses etc.

	# python >= 3.6
    pip install --user -r requirements.txt
    python3 extract.py TEI.xml

## Technical Tools

* [Transkribus](https://transkribus.eu/Transkribus/): *OCR*- Gathering of menus and for the annotation work of food and drinks on the menus.
* [RStudio Shiny-Server](https://www.rstudio.com/products/shiny/shiny-server): R based open-source platform for the web application.
* [Jupyter Notebooks](https://jupyter.org/): Python Functions to import and to clean the Data and to run some statistical analysis.
* [Leaflet](https://leafletjs.com/): JavaScript library for displaying the interactive map(s) in the web application.

## Citation and Reuse

All images of the menus as well as the data resulting from the project are permanently stored in the research data repository of the LMU Munich ([Open Data LMU] (https://data.ub.uni-muenchen.de/)) and clearly referenced by means of a *DOI*: https://doi.org/10.5282/ubm/data.146.


For the citation of the project, or to reuse, we recommend the following:
> Cakir, Osman / Kohl, Linus / Reißer, Alexandra / Schneider, Stefanie / Schulz, Julian: Schmankerl Time Machine: Eine kulinarische Zeitreise durch die Speisekarten traditionsreicher Münchner Gaststätten. 18. Mai 2019. Open Data LMU: https://doi.org/10.5282/ubm/data.146.

A specification of the data in the metadata schema [DataCite 4.2](https://schema.datacite.org/meta/kernel-4/) is [ready](https://gitlab.com/cds19-team/cds19/raw/master/codav_datacite.xml) for reuse. The specification follows the DataCite Best Practice Policy, which is currently being developed as part of the [eHumanities - interdisciplinary](https://www.fdm-bayern.org/) project.

## Contribution

We appreciate your support in annotating additional menus with Transkribus. We have initiated a [Crowdsourcing-Project](https://transkribus.eu/r/read/projects/) for this purpose. Contributions in the form of programs or improvements are very welcome: In this case please open a pull request.

## Team

* **Osman Cakir** ([Website](https://osmancakir.io/), [ORCID](https://orcid.org/0000-0002-4828-0748), [Twitter](https://twitter.com/osmancakirio))
* **Linus Kohl** ([Website](https://munichresearch.com), [ORCID](https://orcid.org/0000-0003-3400-837X), [LinkedIn](https://www.linkedin.com/in/linuskohl), [Twitter](https://twitter.com/LinusKohl))
* **Alexandra Reißer** ([ORCID](https://orcid.org/0000-0001-5560-1901), [LinkedIn](https://www.linkedin.com/in/alexandra-rei%C3%9Fer-379aa7180/), [Twitter](https://twitter.com/alexreisser))
* **Stefanie Schneider** ([Website](https://www.kunstgeschichte.uni-muenchen.de/personen/wiss_ma/schneider/index.html), [ORCID](https://orcid.org/0000-0003-4915-6949), [Twitter](https://twitter.com/_stschneider))
* **Julian Schulz** ([Website](https://www.hgw.geschichte.uni-muenchen.de/personen/mitarbeiter/schulz), [ORCID](https://orcid.org/0000-0003-4374-2680), [Twitter](https://twitter.com/SchJulzian))

## Licences

* Illustrations of the menus were under license [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0) from the Munich City Library / Monacensia im Hildebrandhaus.
* Data generated by the project is also subject to the license [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0).
* Source code is subject to the [GNU GPL v3](https://www.gnu.org/licenses/gpl-3.0.de.html) license.

## Thanks

We would like to thank the organizers of this year's competition and the project coordination of [Coding da Vinci](https://codingdavinci.de/about/index-de.html).
