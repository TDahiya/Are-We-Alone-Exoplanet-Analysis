# Are We Alone? The Search for Earth 2.

**_Authors:_** _Tanishq Dahiya_
**_Module:_** _CSC1143/CSC1 175 Data Visualisation_
**_Date:_** _November 2025_

## Abstract

_This assignment goes deeper into one of the most profound questions in astronomy:
"Are we alone?" By analyzing the physical characteristics of thousands of
exoplanets, we aim to determine how common "Earth-like" worlds are compared to
the vast population of uninhabitable gas giants. We used the official NASA Exoplanet
Archive dataset [1] to visualize the relationship between planetary radius and orbital
distance. Our analysis reveals that while the majority of discovered planets are
hostile environments, a distinct, 1 potentially habitable planet exists. We visualized
this phenomenon using a scatter plot which was further log scaled for better
visualization. With a specialized inset zoom-in feature to label the top unique
candidates in the "Goldilocks Zone."_

## 1. Datasets
```
We acquired the dataset for this study from the NASA Exoplanet Archive, a
comprehensive public database maintained by the California Institute of Technology.
The initial raw dataset contained over 35,000 rows of data. Each row contains
high-dimensional data with over 90 columns of astrophysical parameters
```
## 2. Data Exploration, Processing, and Cleaning
```
To prepare the dataset for visualization, we used Python with the Pandas library
```
## 2.1. Data Cleaning

## 2.1.1. Handling Missing Values

```
The raw NASA data contained significant "noise" (NaN values) because not
all detection methods yield both mass and radius data. We used df.dropna()
to remove incomplete records.
```

### 2.1.2. Removing Duplicates

```
We observed that the raw dataset contained multiple entries for the same
planet (e.g., Kepler-452 b appearing multiple times due to updated
observations). To ensure our count of habitable worlds was accurate, we
applied a filter (drop_duplicates(subset=['pl_name'])) to retain only one unique
record per planet.
```
## 2.2. Data Subsetting (The "Goldilocks" Logic)
```
To tell the story of "Habitability," we created a subset of data based on standard
astrobiological parameters:
● Distance: 0.8 to 1.5 AU (Astronomical Units) The distance where liquid
water can exist.
● Size: 0.8 to 1.5 Earth Radii – The size range where a planet is likely rocky.
● Earth Similarity Sorting: To identify the best candidates for labeling, we
calculated a "Distance Score" for each planet based on how close its
coordinates were to Earth (1,1).
```
## 2.3. Exploratory Analysis

### 2.3.1. Attribute Selection

```
To determine the best variables for our visualization, we analyzed the
completeness of every column in the dataset. This exploratory phase revealed
that while Planetary Mass is scientifically relevant, it suffers from missing
values compared to Planetary Radius. As shown in Figure 1, using Radius
(pl_rade) allowed us to plot nearly 3,619 planets, whereas using Mass would
have reduced our sample size. Based on this evidence, we selected Radius
as the superior attribute for the Y-axis.
```

```
Figure 1: Data Completeness Comparison. Radius data is far more complete
than Mass data.
```
### 2.3.2. Historical Context
```
We also plotted the cumulative discovery rate over time (Figure 2) to verify the
"Volume" aspect of our dataset. The sharp exponential rise after 2010 (largely
due to the Kepler Space Telescope) confirms that we are working with a
modern, high-volume dataset suitable for "Big Data" analysis..
**Figure 2:** _Cumulative discoveries over time. The dataset volume has
exploded in the last decade, providing a rich sample size for analysis._
```

## 3. Visualization

### 3.1. Design Process

```
Our design goal was to visualize a massive disparity in scale. We needed to
show the abundance of planets while simultaneously highlighting the scarcity of
habitable ones.
Figure 3: Initial sketch showing the concept of a main scatter plot with a
"magnifying glass" effect to see the small Earth-like zone.
```
### 3.2. FINAL VISUALIZATION

```
Figure 4: Log Scaled Scatter Plopt of Unique Exoplanet Populations with Inset
Zoom labeling
```

### 4. Justification of Design Choices

#### 4.1. Chart Type

```
Scatter Plot (Log Scaled), we used a scatter plot because it was the best plot we
could find to identify clusters in two-dimensional space.
● Problem: Planetary distances vary from 0.01 AU (scorched worlds) to 100 AU
(frozen worlds). On a linear scale, the "Goldilocks Zone" would be
compressed into a single pixel.
Figure 5: Visualization without Log Scale 'Problem'
● Solution: We applied a Logarithmic Scale. This expanded the "small numbers"
region, allowing us to clearly distinguish between a planet at 0.5 AU and 1.
AU
```
#### 4.2. Measurement Units

```
We used Relative Units rather than absolute units (km) to make the graph
intuitive:
● X-Axis (Astronomical Units): Defined as the distance from Earth to the
Sun. A value of 1.0 places the viewer instantly in a familiar context.
● Y-Axis (Earth Radii): Defined relative to Earth's size. This allows the viewer
to instantly judge if a planet is a "Super-Earth" (1.5x) or a "Gas Giant"
(10x).
```

#### 4.3. The Inset Plot

```
While the logarithmic scale effectively visualized the entire dataset, we
implemented an additional inset plot using mpl_toolkits to enhance the viewer's
experience. This 'Zoom-In' feature focuses specifically on the habitable region,
allowing for easier reading of individual labels and details without losing the
context.
● Function: This secondary plot focuses exclusively on the coordinates
0.7–1.6 (AU/Radii).
● Labeling Strategy: We programmatically labelled only unique planets
closest to Earth's profile. We also labelled all habitable planets making the
chart readable.
```
#### 4.4. Colour

```
● Context: We coloured the general population Gray with high transparency
(alpha=0.15). This represents the volume out of the habitable zone.
● Focus Data: We coloured the habitable candidates Green (#2ca02c) with
solid opacity. Green is semantically associated with life, making it the
intuitive choice for habitable worlds.
● Connection: We used green connecting lines to link the inset box to the
main plot. To represent the zoom in feature is related to habitable zone
```
## 5. Conclusion
```
Tools Used: We used Python programming language with libraries , Pandas handled
the large-scale data cleaning, while Matplotlib was used for the advanced plotting
features.
Critical Analysis: The visualization successfully answers the question "Are we
alone?" by demonstrating that while Earth-like planets are statistically rare (a small
green dot in the whole sea of gray), it definitely exists. The addition of labels for
specific candidate _Kepler-452 b_ added a tangible reality to the abstract data.
Collaboration: Kartik sourced the NASA dataset and researched the definitions of the
Habitable Zone. Tanishq wrote the Python code, specifically implementing the all
logic and the algorithm to see "Earth Similarity" amongst all planets. We collaborated
on the final design layout and report writing.
```

## 6. References

**[1] Dataset:** NASA Exoplanet Archive (2025). _Planetary Systems Composite Data_.
California Institute of Technology. DOI: 10.26133/NEA12
Christiansen et al. (2025). _The NASA Exoplanet Archive and Exoplanet Follow-up
Observing Program: Data, tools, and usage_. **The Planetary Science Journal** , 6,
**Tools:** _Matplotlib: Visualization with Python_ , Pandas



