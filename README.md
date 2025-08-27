# 🚆 SNCF Low Fares 2024 – Data Sprint

Data analysis project on SNCF open datasets, identifying the most affordable train routes in France (TGV INOUI & OUIGO).  
Includes data cleaning, feature engineering (distance, regions), and visualizations to compare fares across routes and profiles.  

---

## 1 - Objective
Measure how SNCF fares vary across routes, regions and fare profiles, and identify which destinations are the most (or least) affordable in €/km.  

## 2 - Data Sources

- **Main dataset**: [Tarifs TGV INOUI & OUIGO](https://ressources.data.sncf.com/explore/dataset/tarifs-tgv-inoui-ouigo/table/)  
  - 15,570 rows  
  - 9 columns (Transporter, Origin Station, UIC code, Destination Station, Class, Fare Profile, Min Price, Max Price)  
  - Provides price ranges (min/max) per route and fare profile (Normal, Student, Regulated)   

- **Additional datasets**:  
  - SNCF “Voyager Stations” dataset (station metadata and regions)  
  - SNCF “CO₂ Emissions” dataset (distances between stations + price/km)  
  - [Atlas GeoJSON](https://france-geojson.gregoiredavid.fr/) (regional boundaries for mapping)
    
---

## 3 - Methodology

**Corpus preparation**  
- Added columns from external datasets:  
  - *Region Name* (from SNCF station locations dataset)  
  - *Fare per km* (from CO₂ emissions dataset)  
  - *Geopoint* (lat/long from station dataset)  
  - *Geo_shape* (regional polygons from GeoJSON)  

**Analysis & visualization**  
- Map stations geographically and associate each with a region  
- Retrieve regional boundaries via GeoJSON  
- Compute average **fare per km per region**  
- Rank regions from most to least expensive  

---

## 4 - Results
- Students benefit from significantly cheaper fares (0.3–0.5 €/km)  
- Some regions (e.g. **Centre-Val de Loire**) are less accessible than others  
- Student fares show strong consistency across regions


  **Key visualizations:**  

### Geographic distribution of fares (map)
![Geographic distribution of fare](Graphs/Geographic_distribution_of_fares_(map).png)

### Average fares by region (bar chart)
![Average fares by region](Graphs/Average_fares_by_region_(bar_chart).png)

---

## 5 - Next Steps
- Extend analysis with a temporal dimension (evolution of fares over time)  
- Compare SNCF fares with other transport modes (bus, car, plane)  
- Explore sociological implications of regional fare inequalities (urban vs rural)  

---

## 6 - References
- C. Alet (2009). *SNCF : un prix peut en cacher un autre*, Alternatives Économiques.  
- J. Finez (2014). *La construction des prix à la SNCF, une socio-histoire de la tarification*, Revue française de sociologie, pp. 5–39.  

---

## License
MIT – Free to use and share with attribution.  
