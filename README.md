# Project Summary

This project applies **Multi-Criteria Decision Making (MCDM)** techniques to build a data-driven framework for ranking bus routes suitable for **Battery Electric Bus (BEB)** deployment. Public transportation systems involve complex operational, environmental, and equity-based factors, making systematic route evaluation essential.

## Dataset

A **GTFS (General Transit Feed Specification)** dataset was used, consisting of several structured text files. While the dataset supported most steps, some mathematical assumptions and data cleaning tasks were necessary.

### Core GTFS Files Used
- **routes.txt** – Definitions of all bus routes  
- **trips.txt** – List of scheduled trips  
- **stop_times.txt** – Stop sequences and departure times  
- **stops.txt** – Geographic coordinates and stop details  
- **shapes.txt** – GPS points representing the geometry of each route  
- **calendar.txt / calendar_dates.txt** – Service days, exceptions, and availability  
- **agency.txt / feed_info.txt** – Metadata about the transit agency and dataset validity

## Step 1: Data Processing

Using **pandas** and **NumPy**, the necessary GTFS files were loaded and cleaned.

Key operations:
- Converted time fields to seconds and validated coordinate formats  
- Removed invalid or inconsistent rows  
- Counted total trips per route using `trip_id`  
- Calculated average route distance using the **Haversine formula** applied to shape points  
- Computed **average headway** (mean departure interval) from `stop_times.txt`  
- Combined all metrics into a summary table  

## Step 2: Route Ranking with TOPSIS

The **TOPSIS** method (Technique for Order Preference by Similarity to Ideal Solution) was used to rank BEB-suitable routes.

Process details:
- Randomly generated values for **Equity** and **Elevation** criteria  
- Classified each criterion as either a benefit or cost based on judgement  
- Adjusted criteria weights (optional task) using subjective reasoning  

## Step 3: Visualization

A **matplotlib** bar chart was created to visualize the ranking results and compare route scores.
