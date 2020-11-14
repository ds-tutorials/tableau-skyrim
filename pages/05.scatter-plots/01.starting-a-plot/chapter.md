---
title: 'Starting a Plot'
taxonomy:
    category:
        - docs
visible: true
intro:
    level: beginner
---

## Scatter Plots

While bar charts are good for displaying one measurement for categorical data, they are not nearly so helpful for comparing different measurements to each other. For example, endorsements and downloads are two interesting measures we have not worked with yet. If we want to see how they relate to each other, even a side-by-side bar chart (where each category has two bars, one for endorsements and one for downloads) will not be very helpful in making any meaningful comparisons. Further, if we want to examine the relationship between the two measures for individual mods, rather than for entire categories of mods, we would be out of luck. We would need 10,000 bars! Instead, we will make use of the scatter plot, an excellent type of chart for finding the correlation between two measurements.

In this section we will make two scatter plots. The first will compare Endorsements to Total Downloads, and the second will compare a calculated field we will call Approval Ratio to Total Downloads.

Our goal for the Endorsements scatter plot is to compare the endorsemens a mod receives with the total number of times that mod is downloaded. How are the two measures related to each other? My initial assumption is that they would be heavily correlated, with high total downloads corresponding to high endorsements, but how related will they be and how much variation will there be? Another interesting question is: Which mods stand out within these measures? There are sure to be a few outliers, data points that do not fall within the same area as the majority of points.

Our goal for the first scatter plot is to compare the endorsements a mod receives with the total number of times that mod is downloaded. How are the two measures related to each other? My initial assumption is that they would be heavily correlated, with high total downloads corresponding to high endorsements, but how related will they be and how much variation will there be? Another interesting question is: Which mods stand out within these measures? There are sure to be a few outliers, data points that do not fall within the same area as the majority of points.

!!!! ## Learning Objectives
> 
> - Make a scatter plot.
> - Use **Columns** and **Rows** to add dimensions/measures to a worksheet.

## Endorsements Scatter Plot

1. Click on the _New Worksheet_ button.
2. Right click the new worksheet and rename it _Endorsements_.
3. Note that on the left we still have sections for both mods.csv data and tags.csv data. If you collapsed mods.csv for convenience while building the Top Tags bar chart, you will now want to collapse tags.csv and expand mods.csv.

! What happens if we use tags.csv instead of mods.csv? We will be creating a point in the plot for each mod. In mods.csv, one record corresponds to one mod, so this will be a straightforward process. In tags.csv, many mods will have multiple records, so our default solution would end up adding together the endorsements and downloads for each of these records, creating extremely inflated values based on the number of tags a mod uses. Changing from sum to average values might be the perfect solution to this, although it does add an extra step, but some mods may not have tags at all. These mods would not be in our tags dataset. The only solution for this issue (that does not involve creating a new dataset) is to use the mods dataset.

### Adding Data

Scatter plots rely more heavily on the **Rows** and **Columns** fields (found at the top of the application) than our previous charts did. However, it is not necessary to know how we want the data arranged. We will prove this by adding both our measures to the **Rows** field.

1. Locate _Endorsements_ under mods.csv on the **Data** sidebar and drag it onto **Rows**.
2. Locate _Total Downloads_ under **Measures** and drag it onto **Rows** as well.
![Endorsements and Total Downloads in Rows. Nothing in Columns.](01.rows.png?cropResize=650,150)
3. Click on **Show Me** and choose the scatter plot option. Note that this is currently the recommended option. After choosing scatter plot, Tableau will automatically move one of our measures to **Columns**.
![Changing chart type to scatter plot.](02.show-me-scatter-plot.png?cropResize=300,750)
4. For this chart we want endorsements to be plotted along the y-axis (horizontal). Theoretically this means we would be observing how endorsements vary depending on number of total downloads. If endorsements were along the x-axis (vertical) instead, we would be observing how total downloads vary depending on number of endorsements. In some ways this is all semantics, but it still does matter. Check to make sure that _Endorsements_ is in **Rows** (and that _Total Downloads_ has been moved to **Columns**).
![The Rows and Columns boxes](03.endorsements-rows.png?cropResize=450,200)
5. If Tableau moved _Endorsements_ instead of _Total Downloads_ to **Columns**, click the _Swap Rows and Columns_ button from the toolbar. This is a handy button to be aware of when making many types of charts.
![The Swap Rows and Columns button](04.swap-rows-cols.png?cropResize=450,200)

This is the resulting chart:

![A scatter plot with one point](05.single-point-plot.png?cropResize=800,900)

### Displaying Multiple Points

Unfortunately, we only have one point on our chart. This is because Tableau does not know how to group our data. By default, it is treating everything in the dataset as one group, and therefore one point, taking the sum of all endorsements and the sum of all total downloads from the dataset. If we want it to do something different, we will have to tell Tableau how to group the data. Do we want a point for each category? For each country? For each mod? Since we do want a point for each mod, we need some kind of unique identifier so that no mods will accidentally be grouped together. This is another situation where Mod ID is extremely useful. In a pinch, we could perhaps use the mod names, but we do not have a guarantee that these will always be different.

1. Locate _Mod ID_ under mods.csv on the **Data** sidebar.
2. Drag it onto the Detail box on the **Marks** shelf.
![The Detail box](07.marks-detail.png?cropResize=400,400)

Now we should see a point for each mod. As we can see, endorsements and total downloads are indeed heavily correlated. The most extreme outlier in our dataset, the point at the top right, is for the mod [SkyUI](https://www.nexusmods.com/skyrim/mods/3863), a complete overhaul of the Skyrim user interface.

![A scatter plot with many points, most going diagonally from the bottom left to the top right](08.many-point-plot.png?cropResize=800,900)