---
title: International Sanctions Network
summary: Visualizing the web of sanctions that countries have imposed on each other using Python and network analysis.
tags:
  - Python
  - Social Network Analysis
date: 2023-08-15

authors:
- admin

links:
  - name: Read Project
    url: '/project/international-sanctions-network/'
  - name: View Code
    url: https://github.com/macuriels/umass_dacss_datastorytelling/blob/main/international_sanctions_network.ipynb
  - name: Download Dataset
    url: https://macuriels.com/files/international_sanctions_network.xlsx

image:
  caption: Image generated using Canva's Text to Image AI generator
  focal_point: Smart
---

{{% callout note %}}

**PROJECT SUMMARY**

- Sanctions are increasingly common forms of pressure employed by governments. A network of country-level sanctions is visualized using data from 1950 to 2022.

- The dataset is wrangled and results in 153 countries and 726 sanctioning relationships. This data is used to create a network of sanctioning/sanctioned countries.

- There are three main dynamics present in the network of international sanctions: the sanctioning powerhouses, the regional communities, and the wildcards. 

- The powerhouses are those who have issued the most sanctions and are in the center of the network; the regional communities are close together in the network and in geography; and the wildcards are close to the powerhouses and have the potential of acting as mediators, allies, or instigators.

- Although the network analysis yields interesting roles and groupings, future endeavors could benefit from procuring a more robust analytical approach.

{{% /callout %}}

---

Sanctions are forms of pressure that governments impose on other countries or organizations in response to actions that are deemed unacceptable, such as human rights violations or terrorism. 

Even though sanctions have been brought into the limelight in the last decade, they are not a new practice. In fact, the first sanction arguably dates back to a BC era, when the then-independent state of Megara was banned from trading in Greece’s marketplace.

Fast forward to present day. The current geopolitical landscape - which includes ongoing wars, forced labor, near-shoring, to name a few - is bound to be intertwined with countries imposing sanctions on one another. 

This article is brings a novel approach to understand the geopolitical landscape by **analyzing the network of international sanctions** based on current and historical data to assist policy-makers, researchers, and curious bystanders. 

The article is divided as follows:
1. Methodology
2. Exploratory Analysis
3. Network Analysis
4. Conclusions

---

# Methodology

This analysis explores trends in international sanctions since 1950 using an open-source dataset, the [Global Sanctions Data Base](http://www.globalsanctionsdatabase.com/) (or GSDB). 

The GSDB's most recent release - its third edition - contains sanctions until 2022, encompassing sanctions imposed due to COVID-19 and the war between Russia and Ukraine.

The original database contains 1,325 cases of countries and international organizations issuing sanctions against each other. Additional wrangling of the dataset is performed using the programming language Python.

## Data Collection

The researchers collect data by cross-referencing across diverse official sources, from government orders to international newspapers and history books. 

Besides the sanctioning and the sanctioned government, the dataset contains other variables such as the start and end dates of the sanction, the objective of the sanction, and its outcome. 

Even though the most common are trade sanctions, the database also differentiates between other types, such as military and travel bans.

## Data Wrangling

This analysis omits and summarizes several variables from the original dataset. The data wrangling results in a table with nodes and edges (countries and sanctioning relationships, respectively).

{{< spoiler text="*Click to view the data wrangling operations*" >}}

- Renaming countries for smoother processing and visualization (e.g., changing “Congo (Brazzaville)” to “Republic of the Congo”).

- Converting multilateral sanctions into dyadic relationships (e.g., in the original database, if the US and Canada both issued a sanction against Russia, the US and Canada will appear in the same row; the preprocessing makes it so that they are spread across two rows).

- Removing dissolved countries (e.g., Yugoslavia) and international organizations (e.g., the United Nations).

- Adding 2-digit country codes (ISO 3166), continents, and URLs leading to each country’s flag to enhance the data visualization.

- Create a list of distinct nodes (countries that either sanction or have been sanctioned) and edges (pairs of sanctioning and sanctioned countries).

- Each node has its degree calculated (a measurement that considers how many times a country has been on either end of the sanctions, i.e., how many times it has been sanctioned and how many times it has issued a sanction).

- And each edge has a weight (the sum of how often one country sanctions another, e.g., if the USA has sanctioned Russia twice since 1950, this relationship will receive a weight of 2).

{{< /spoiler >}}

A full script with the data wrangling code can be viewed on the following Jupyter Notebook:
https://github.com/macuriels/umass_dacss_datastorytelling/blob/main/international_sanctions_network.ipynb

The tidied data is used to create a network visualization and view the web of sanctions among countries. The network is created and hosted through Fluorish’s interactive software. Some additional plots and tables are created using Python to explore the dataset.

---

# Exploratory Analysis

The tidied dataset contains 153 distinct countries that have either sanctioned or been sanctioned and 726 distinct pairs of sanctioning relationships. Below is the breakdown by continent.

| **CONTINENT** | **COVERAGE**                            |
|---------------|-----------------------------------------|
| AFRICA        | 40 countries (74% of countries covered) |
| ASIA          | 42 countries (86% of countries covered) |
| EUROPE        | 41 (93% of countries covered)           |
| NORTH AMERICA | 16 (70% of countries covered)           |
| OCEANIA       | 4 (29% of countries covered)            |
| SOUTH AMERICA | 10 (83% of countries covered)           |

The dataset has decent coverage across most continents, with Oceania being the exception. Rather than this being a quality issue with the database, this is most likely due to Oceania being less involved in sanctions.

Another approach to explore the data is through an overview of sanctions over time. 

{{< chart data="country-sanctions-sum" >}}

From the line chart, we can see that these remained relatively low from 1950 to 1980. 

There’s a slight increase in the 80s, corresponding to Iran’s Hostage Crisis, the Soviet Invasion of Afghanistan, and Cold War Dynamics in general. 

Sanctions really pick up the pace from the turn of the millennia - which mostly corresponds to the sanctions following 9/11.

Another notable spike in sanctions activity occurred in 2011, which involved a mixture of relevant international events, namely the Arab Spring Uprisings, the beginning of the Syrian Civil War, and the dictatorship in Libya. 

From there, the most prominent spike happens in 2022 and is a direct response of Western countries against Russia amidst its invasion of Ukraine.

---

# Network Analysis

After generating a list of nodes and edges, the network is generated using a simple repulsion-attraction algorithm, i.e., related nodes will be closer together, and more connected nodes will be in the center. 

The network is also stylized by increasing the node size according to its degree; the edge width corresponds to the times a sanctioning relationship has occurred; and the colors behind the flags represent the continents.

{{% callout note %}}

The network is interactive. Users can hover over nodes to see additional information or drag them around the network to experiment with different layouts.

{{% /callout %}}

<div class="flourish-embed flourish-network" data-src="visualisation/14725057"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

## Powerhouses

Some elements that can immediately draw attention are the central nodes of the system - primarily the United States, followed by the United Kingdom and Canada. 

Prominent nodes in a network can be considered gravitational centers because they maintain a system together, exert strong influence, and guide other nodes. 

In this context, influential nodes are **sanctioning powerhouses** that lead by example and align with one another. For example, many of the countries sanctioned by the US are also sanctioned by the UK and Canada.

## Communities

Countries further from the center tend to form clusters of sanctioning/sanctioned countries, and these clusters correlate to geographic regions. 

These clusters can be considered sanctioning communities that are determined by **regional dynamics**. 

For example, there is one cluster of Eastern European countries (such as Albania, Macedonia, Moldova, and Armenia) that tend to sanction the same African countries (such as Zimbabwe, Sudan, and Côte d'Ivoire). 

Another noteworthy community is the one formed around Qatar - this country has a handful of countries solely connected to it, meaning that they sanctioned Qatar (which correlates to Qatar’s diplomatic crisis circa 2017).

## Wildcards

Lastly, some nodes are not influential nor are clustered according to geographical region but are central to the network. 

Under network science, these are close to the gravitational centers, so they can be considered influential by extension.

In terms of sanctions, these can be interpreted as **powerful-adjacent wildcards**, as they have the influence to align with existing alliances or form new ones, hence having the potential of acting as mediators or instigators.

Most of these are Latin American and Caribbean countries - e.g., Panama, Ecuador, Uruguay - that could either act as mediators or further cement alliances in the international sanctions network.

---

# In Conclusion

This brief exercise demonstrates a network of international sanctions. This system is characterized by sanctioning powerhouses, regional communities, and potential instigators of conflict or resolution.

The sanctioning powerhouses are central to the network and exert strong influence by leading by example. These nodes are English-speaking countries with high socioeconomic status (i.e., the US, the UK, and Canada).

The network also unveils clusters that determine that countries in geographic proximity to each other implement similar sanctions, such as Eastern European countries that sanction the same African countries. 

Lastly, the nodes that are central in the network but have a low degree of connectedness correlate with Latin American and Caribbean countries, which have been involved in less sanctioning activity and have the potential to serve a more prominent role in the system.

## Future Considerations

However interesting these findings may be, there are some significant limitations to keep in mind. 

For starters, not all variables from the original dataset were used; therefore, this model likely employs a simplistic approach to a multi-faceted problem. 

Additionally, it can be worth thinking about a better way of treating dissolved countries and international organizations, as these have played a role in developing the current sanctions landscape but are omitted from this model. 

Lastly, the network model underlying the visualization is a simple repulsion/attraction calculation - it may be worth exploring alternative algorithms and analyzing how the distribution changes.

