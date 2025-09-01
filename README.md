# 🚆 SNCF Low Fares 2024 – Data Sprint (*academic project*)

Data analysis project on SNCF open datasets, focusing on the geography of trains fares in France (TGV INOUI & OUIGO).  
Includes data cleaning, feature engineering (distance, regions), and visualizations to compare average fares per kilometre across French regions.  

---

## 1 - Objective
Measure how SNCF fares vary geographically by calculating the average fare per kilometre (€/km) by destination region, and identify which destinations are the most and least affordable.  

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
- Converted SNCF fares into fare per kilomtre
- Merged with station metadata to link each destination station to its region. Added columns from external datasets:  
  - *Region Name* (from SNCF station locations dataset)  
  - *Fare per km* (from CO₂ emissions dataset)  
  - *Geopoint* (lat/long from station dataset)  
  - *Geo_shape* (regional polygons from GeoJSON)  

**Analysis & visualization**  
- Map stations geographically and associate each with a region  
- Retrieve regional boundaries via GeoJSON  
- Compute average **fare per km per by destination region**  
- Rank regions from most to least expensive  

---

## 4 - Results
•	Clear regional differences by destination:
	•	Trips to Hauts-de-France, Île-de-France, Auvergne-Rhône-Alpes are the most expensive (≈ 0.26 €/km).
	•	Trips to Pays de la Loire, Nouvelle-Aquitaine, Bourgogne-Franche-Comté are the least expensive (< 0.20 €/km).

  **Key visualizations:**  

### Geographic distribution of fares (map)
![Geographic distribution of fare](Graphs/Geographic_distribution_of_fares_(map).png)

### Average fares by region (bar chart)
![Average fares by region](Graphs/Average_fares_by_region_(bar_chart).png)

---

## 5 - Discussion

The observed regional disparities (≈ €0.09/km between cheapest and most expensive destinations) confirm that SNCF fares ares not driven only by distance. 
As Finez (2014) shows, pricing results from a shift towards yield management, where fares adapt to demand.
Similarly, Alet (2009) highlights the opacity of SNCF pricing, which conceals marked territorials inequalities. 
Our results reflect this: high-demand regions (Île-de-France, Auvergne-Rhône-Alpes) are structurally more expensive, while others remain more affordable. 

---

## 6 - Next Steps
- Extend analysis with a temporal dimension (evolution of fares over time)  
- Compare SNCF fares with other transport modes (bus, car, plane)  
- Explore sociological implications of regional fare inequalities (urban vs rural)  

---

## 7 - References
- C. Alet (2009). *SNCF : un prix peut en cacher un autre*, Alternatives Économiques.  
- J. Finez (2014). *La construction des prix à la SNCF, une socio-histoire de la tarification*, Revue française de sociologie, pp. 5–39.  

---

## License
MIT – Free to use and share with attribution.  
