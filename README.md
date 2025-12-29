# The Garibaldi at Squamish: A Terrain Suitability Analysis

**Author:** Natalie Skupchenko  
**Course:** GEOS 270 (Geographic Information Science) - Term Project  
**Term:** February 2025 - April 2025  
**Tools:** ArcGIS Pro (data tables, SQL queries), Excel

**View the story map here: https://arcg.is/1uHf1C4**

**Download the full PDF report here: [The Garibaldi at Squamish: A Terrain Suitability Analysis (PDF)](PDF_StoryMap.pdf)**

---

## Project Overview

This project applies **constraint-based spatial modeling** to assess development viability for a proposed ski resort near Squamish, BC. I extended a course lab assignment into a comprehensive term project by integrating multiple spatial datasets, performing raster-vector analysis, and creating an interactive data visualization to communicate findings.

**Research Question:** Given environmental protection requirements and climate constraints, what percentage of the proposed resort area is actually viable for development?

**Key Finding:** Only **32%** of the proposed 2,847-hectare area meets both climate suitability and environmental protection criteria—significantly less than project proponents suggest.

### Why This Matters

The Garibaldi at Squamish proposal claims the area can support 124 ski trails, 21 lifts, and 2,500 operational jobs. However, environmental agencies and neighboring municipalities have raised concerns about habitat disruption and climate viability. This analysis uses spatial data to quantify those concerns.

---

## Technical Approach

### Data Sources (7 spatial datasets)

| Dataset | Type | Source | Use in Analysis |
|---------|------|--------|----------------|
| Digital Elevation Model | 20m raster | TRIM (via UBC Library) | Climate suitability (>600m snowline) |
| Ungulate Winter Range | Polygon | DataBC | Wildlife habitat protection |
| Old Growth Management Areas | Polygon | DataBC | Forest conservation areas |
| Rivers & Streams | Line | TRIM | Fish habitat identification |
| Roads | Line | TRIM | Access infrastructure |
| Contours (20m) | Line | TRIM | Topographic visualization |
| Project Boundary | Polygon | Provided | Study area definition |

**Note:** TRIM (Terrestrial Resource Information Management) data is normally $600 per mapsheet for the public; accessible to UBC students through library agreement.

### Analysis Workflow

**1. Data Acquisition & Preparation**
- Downloaded 2 datasets from BC Data Catalogue (DataBC)
- Accessed 5 pre-processed TRIM datasets from course materials
- Standardized coordinate systems (NAD 83 UTM Zone 10N)
- Organized datasets in ArcGIS geodatabase

**2. Spatial Data Processing**

*Climate Suitability (Elevation Analysis):*
- Clipped elevation raster to project boundary
- Reclassified DEM into binary classes: <600m (unsuitable) vs. ≥600m (suitable)
- Converted raster to polygons for area calculations
- **Result:** 68% of area above 600m threshold; 32% below snowline

*Environmental Constraints:*
- Clipped wildlife habitat, old growth, and rivers to project area
- For **variable-width buffering** of fish habitat:
  - Used "Add Surface Information" tool to assign elevation values to river segments
  - Created calculated field: 100m buffer below 600m, 50m buffer above 600m
  - Generated protection zones around all streams
- **Result:** 28% fish/riparian, 8% wildlife habitat, 7% old growth

*Integrated Constraint Analysis:*
- Used Union overlay to combine all protection layers
- Dissolved overlapping areas to avoid double-counting
- **Result:** 39% of total area falls within protected zones

**3. Composite Viability Assessment**
- Overlaid climate suitability with environmental constraints
- Identified areas that are BOTH above snowline AND outside protected zones
- **Final Result:** Only 32% of area is developable under current constraints

**4. Secondary Analysis (Alpine Terrain)**
- Isolated alpine/sub-alpine zones (expert terrain)
- Overlaid with avalanche terrain and protected areas
- **Result:** Only 4.2% of total area is safe, unprotected alpine terrain

### Key Techniques Used

- **Raster reclassification** - Binary classification of continuous elevation data
- **Attribute-based buffering** - Variable buffer widths based on stream elevation
- **Vector overlay analysis** - Union operation to combine multiple constraint layers
- **Spatial aggregation** - Dissolve to merge overlapping protection zones
- **Area calculations** - Converting spatial extents to percentage metrics
- **Raster-to-vector conversion** - Polygon generation from classified elevation

---

## Results Summary

### Quantitative Findings

| Constraint Type | % of Total Project Area |
|----------------|------------------------|
| Fish/riparian habitat | 28% |
| Wildlife winter range | 8% |
| Old growth forest | 7% |
| **Total Protected Area*** | **39%** |
| Below 600m elevation (climate risk) | 32% |
| Above 600m (climate suitable) | 68% |
| **Viable & Unprotected** | **32%** |

*Note: Total protected area (39%) is less than sum of individual protections (28% + 8% + 7% = 43%) due to overlapping zones*

### Contextual Analysis

**Comparison to Whistler Blackcomb:**
- Garibaldi's alpine/sub-alpine terrain: 9% of total area
- Whistler's expert terrain: 45% of two-mountain area
- Whistler features: 16 alpine bowls + 3 glaciers

**Implication:** Even if all alpine terrain were developed, Garibaldi would have significantly less expert terrain than its primary competitor 40 minutes north.

### Data Limitations & Uncertainties

1. **Temporal factors:** Wildlife ranges and snow lines may shift with climate change
2. **Resolution:** 20m DEM may not capture micro-terrain features
3. **Binary constraints:** Real planning involves degrees of restriction, not just yes/no
4. **1974 snowline data:** The 600m threshold comes from a 50-year-old report; actual snowpack patterns may differ

---

## Skills Demonstrated

### Spatial Analysis
- Multi-layer constraint modeling
- Raster and vector data integration
- Attribute-based spatial operations (conditional buffering)
- Overlay analysis with area calculations

### Data Management
- Working with government spatial data repositories (DataBC)
- Coordinate system standardization across multiple sources
- Geodatabase organization and file naming conventions
- Handling both raster and vector data formats

### Quantitative Communication
- Converting spatial extents to percentage metrics
- Area calculations with uncertainty acknowledgment
- Comparative benchmarking (vs. existing resorts)
- Creating visualizations for non-technical audiences

### Tools & Software
- ArcGIS Pro (geoprocessing tools, spatial analyst)
- ArcGIS StoryMaps (interactive web mapping)
- Excel (summary statistics)

---

## Project Deliverables

1. **Interactive Story Map** - Web-based visualization with narrative explanation
2. **Technical Report** (PDF) - Detailed methodology and findings
3. **Analysis Geodatabase** - Processed spatial datasets and calculated layers
4. **Static Maps** - 2D and 3D hillshade visualizations with constraint overlays

---

## Learning Outcomes

### Technical Skills
- How to acquire and integrate spatial data from multiple government sources
- The importance of understanding data resolution and accuracy limitations
- How raster and vector operations can be combined for complex analysis
- Creating buffers based on attribute values (not just fixed distances)

### Domain Knowledge
- Environmental planning constraints (riparian zones, wildlife habitat, old growth)
- Climate change implications for ski resort viability
- Trade-offs between economic development and environmental protection

### Communication
- Translating technical GIS analysis into actionable insights for decision-makers
- Visualizing spatial data for public consumption (Story Map)
- Acknowledging uncertainty and data limitations

---

## Potential Extensions

If continuing this project, I would:
1. Conduct temporal analysis of snowpack data (past 50 years)
2. Model future snow conditions under climate scenarios
3. Perform economic analysis: does 912 viable hectares support 2,500 jobs?
4. Analyze infrastructure costs (roads, lifts) in remaining viable terrain
5. Compare to other ski resort proposals rejected/approved in BC

---

## References

**Data Sources:**
- DataBC: British Columbia open data portal ([data.gov.bc.ca](https://data.gov.bc.ca))
- TRIM: Terrain Resource Information Management (via UBC Library)
- HectaresBC: Land use classification data

**Background Research:**
- BC Environmental Assessment Office Report (2010)
- Resort Municipality of Whistler opposition letter (2015)
- Historical climate study (1974) on elevation/snow reliability

**Comparative Data:**
- Whistler Blackcomb mountain statistics ([whistlerblackcomb.com](https://www.whistlerblackcomb.com))

---

## Reproduction Notes

This analysis can be reproduced with:
- ArcGIS Pro (Spatial Analyst extension)
- Access to DataBC and TRIM data
- Study area: NTS mapsheet 92G14 (1:250,000 scale)

Key processing steps:
1. Clip all datasets to project boundary
2. Reclassify DEM at 600m threshold
3. Create attribute-calculated buffers for streams
4. Union all protection layers
5. Overlay climate suitability with environmental constraints

--
