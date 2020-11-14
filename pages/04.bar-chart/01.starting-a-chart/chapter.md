---
title: 'Starting a Chart'
taxonomy:
    category:
        - docs
visible: true
intro:
    level: beginner
---

Our goal in this section is to see which tags are most popular. Each mod may have many tags associated with it, so the required data is stored in a different file in our dataset: tags.csv.

!!!! ## Learning Objectives
!!!! 
!!!! - Work with multiple data sources at once.
!!!! - Join datasets.
!!!! - Create a simple bar chart.

## Using Multiple Data Sources

Because the tag data we want to use for our bar chart is stored in a different file, we need to know how to work with multiple data sources. Because tags.csv is in the same folder as mods.csv, this will be fairly straightforward.

1. At the bottom left of the application, click on the "Data Source" tab.
![Data source tab](01.data-source.png)
2. Find tags.csv below mods.csv under **Files** in the left section.
![tags.csv](02.tags-csv.png)
3. Drag tags.csv onto the top section where it says: "Need more data? Drag tables here to relate them. Learn more." The exact spot where you drag it doesn't matter. This will add a tags.csv box, connected to the mods.csv box with a warning symbol.
![Add tags.csv data](03.add-tags.png)
4. Tableau will now ask us to define the relationship between mods.csv and tags.csv so that it knows which row from the mods dataset holds the relevant data for a given row from tags. Because Mod ID is a unique identifier, it is the perfect choice for something like this. Choose _Mod ID_ from mods.csv on the left and _Mod ID (tags.csv)_ from tags.csv on the right.
![Relate mods.csv and tags.csv using Mod ID](04.define-relationships.png)
5. Click the X at the top to close.

Tableau will now show us the data from tags.csv, like it did when we connected to mods.csv. Many of the columns are the same as what we have seen before, but there is now a column for _Tag_. There are also many instances of the same mod. For example, the mod with ID 11 has multiple rows, one for each tag associated with the mod.

![tags.csv data](05.tags-data.png)

If you are familiar with the concept of joins, what we have done is somewhat similar. By telling Tableau how mods.csv and tags.csv are related, Tableau is now equipped to join the two tables in whatever way we need without any additional input. If you are not familiar with joins, there is no need to be, because Tableau is handling all of this behind the scenes.

Having these two tables related will allow us additional filter functionality later on. We could create our bar chart with only the data from tags.csv, but by relating that data to the mods.csv data, we can relate the bar chart we will make with our map and any other visualizations we create.