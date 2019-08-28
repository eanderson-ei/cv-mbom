# To Dos

- [ ] Formalize business-as-usual notebook 

  - [ ] wrap bootstrap code in function 

     > This allows for the notebook to be called from another notebook if needed, daylights parameters as inputs to the bootstrap, and provides access to the function if needed in other notebooks once run using the magic %run

  - [ ] develop basic visuals to interrogate results for accuracy, completeness
  - [ ] improve documentation within notebook

- [x] Create optimized-outcomes notebook

- [ ] Develop visualizations for report in viz notebook (should work regionally or as aggregated)

- [ ] Develop mapping for report in spatial notebook with folium or in arcgis with arcpy

- [ ] Export code to Markdown > pdf

- [ ] Draft report of outcomes

# Architecture

* cv-mbom
  * data > all inputs
  * notebooks > notebooks for data exploration and presentation of results
  * other > related files not needed for analysis
  * outputs > all outputs (esp. region-level trials data)
  * spatial > spatial data
  * .gitignore
  * README.md
  * TODO.md



1. create per region table of bootstrap trials
2. create per region table of optimization, allowing customizing weights (consider ipywidgets)
3. aggregate per region business-as-usual and optimized-outcomes across all regions (`pd.concat([table1, table2])`)
4. visual difference between optimized-outcomes and business-as-usual
5. map optimized-outcomes 
6. document findings in report format
7. document code as supplements to report
8. moonshot: deploy interactive dashboard with user weights and responsive map output

