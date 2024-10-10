# Solar Panel Generation Data Analyzation

![Data Visualization of solar data](/solardata.png "Solar Power Generation")

## Contributors

Alexander Pirouznia, Carl Chen, Allison Yin, Haneul Song

## Description

The data for this project was sourced from a Kaggle dataset created in 2019 found [here](https://www.kaggle.com/datasets/anikannal/solar-power-generation-data/data). Included was data collected from 2 solar power plants in India over a 34 day period. Each solar plant included generation information where AC Power, DC Power, daily yield, and total yield was collected every 15 minutes. Additionally, weather sensor data was collected for both solar plants where ambient temperatures, module temperatures, and irradiation levels were collected every 15 minutes.

For this analysis, we were interested in examining how energy yield levels were impacted by key environmental factors. In doing so, we narrowed down the datasets into modular temperatures, irradiation, and total yield. Modular temperature is the data collected directly from the module attached to the sensor panel thus seemingly having the most influence on solar energy production when it comes to temperatures. Another key component to solar energy production is irradiation which is the amount of energy from the sun reaching the surface of the panels. Finally, we chose to focus on total yield because we wanted to display the total energy yield of both plants among the other variables.
With the datasets of Plant 1 and Plant 2 weather sensor and generation data, it was important that we implemented a Promise.all call to load all the csv files together. This was because we were using data values from all four of these csv files to create our data visualization. Promise.all let us load the following csv files together all at once.

Then, we deemed it easiest to extract the individual data values we needed and combine them into a new combined dataset for both plant 1 and 2. This would provide us a simpler foundation for the rest of the data visualization and in identifying the domain and range when using d3 features. To do this, we used the Javascript map function to extract individual columns from the data array, such as irradiation, module temperature, and total yield. Next, we wanted to convert them to numeric values by using the data conversion operator “+” so they could be parsed correctly. Then using the data.forEach function, we were able to create a new data array by iterating through the extracted values for Plant 1 and 2. For each index, we appended the extracted data values for temperature, yield, and irradiation for each of the two plants.

With this new dataset, we were able to use the method we learned in class to build scales for the Combined dataset. For yScale, we decided on a log scale instead of a linear scale because it was better for handling data with large ranges, which was apparent with the differences in data values between plant 1 and 2. This is also represented in our data visualization screenshot. Furthermore, it emphasized proportional changes between Plant 1 and 2. It was a better representation of skewed data, as we can see, plant 2 has more scattered values and a much larger range. The log scale allowed us to compress outlier values and stretch out clustered values, providing a more balanced visualization.

Lastly, with the margins in mind and using the previously constructed scales, we were able to construct the gridlines. As a refined touch, we created labels for the axes and added annotations for the gridlines.

## Design Rationale

We chose to represent our data with a scatterplot, with circles as the marks. We used the Module Temperature as the x-location of each point, as this is one of the independent variables. The y-location of each point is determined by the Total Energy Yield, as this is the dependent variable in our data. We also wanted to show the irradiation of each point, and chose to do so through the radius of the circles. Lastly, in order to differentiate between the two solar plants, we colored the points using the “fill” attribute, varying the color hue depending on the plant. We used an ordinal scale with a range of 2 colors because the Plant is a categorical variable with 2 possible values.

We utilized several visual channels to observe the influence of multiple independent factors at once, in the same graph. However, this brought some challenges with the design of our graph. First, the data for solar plant 1 has a much smaller range in total energy yields than solar plant 2. By having the data for both plants on the same scale, it is difficult to see changes in the total energy yield for plant 1 due to its small range. However, we felt that the ability to compare the plants with one another outweighed this challenge. Thus, we kept the data for both of the plants on the same graph.

In addition, the values of total energy yield are clustered around certain values, with large gaps in the range of data. This leaves some y-values highly represented and others with no data points. To better observe the individual data points, we reduced the opacity of the circles to 0.25. This allows us to see any overlaps in data points, providing insight into common values for module temperature and total energy yield. To further support visibility, we added a stroke to each circle with an opacity of 0.5. The opacity of the stroke is higher than that of the circles in order to clearly distinguish between data points. However, it is reduced from its default value of 1 to avoid blocking relevant data.

## The Story

Our visualization reveals the intricate relationship between environmental factors and the energy yield of two solar power plants in India. By comparing module temperature, irradiation levels, and total yield, we can see how these variables impact solar energy production.

One surprising aspect of our analysis was the extent to which module temperature affected total yield. We found that even small fluctuations in temperature had a significant impact on energy output, emphasizing the need for effective temperature management in solar installations.

The key insights we want to convey to viewers are that understanding these environmental influences is crucial for optimizing solar energy production. Our visualization demonstrates how variations in temperature and irradiation levels lead to substantial differences in energy yield, offering stakeholders valuable data to enhance operational strategies and improve the efficiency of solar power plants. 