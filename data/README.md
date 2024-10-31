# Data directory

This is where data required to create figure is stored. It is meant to be self-contained, and include all information 
displayed in the figure. The data included here should require no substantial transformation to be used in the figure.
This means for example that data units should match figure units.  

This directory should be organized as follows:
- This `README.md` file, providing a high level overview of the data included, and how it was prepared from original sources;  
- A `CITATION.cff` file, providing citation information for the data included in this directory (title, authors, references, etc);
- A `LICENSE` file, providing licensing information for the data included in this directory. Should be CC-BY-4.0, please contact the TSU otherwise;
- Clearly named files and/or directories containing the data required to create the figure. If the figure contains multiple panels, 
  data for each panel should be stored in a separate file or directory.

Include any additional instruction on accessing data in this README.

Note: To create the WGI Annex I: Observational products, the information in AR6 is

| Name | Version | Type | Resolution (time and space) | Section(s) | Time Period | Citation, Link and DOI |

## Example `CITATION.cff` file

TODO: Explain what to put in each field. 
`references` should be input data (and possibly key software used). I think one way to organize the content of this
directory and link it to input data is to say: 
- list each input source data file in the `references` section;
- if an input is used to generate multiple files, create a subdirectory with this input name;
- enter the directory or filename generated from the input data in the `filename` field of the `reference` section.

```yaml
title: "Data for AR7 SRC Figure 5.1"
abstract: "Data used to create Figure 5.1 in the IPCC AR7 SRC" 
authors:
- family-names: "Lastname"
  given-names: "Firstname"
  orcid: "https://orcid.org/0000-0000-0000-0000"
version: 1.0
doi: "https://doi.org/10.0000/zenodo.0000000"
references:
- title: Historical CO2 Record from the Vostok Ice Core
  authors:
  - name: J.M. Barnola et al.
  type: data
  data-type: CSV
  filename: data/vostok-ice-core/vostok.icecore.co2
  version: 1.0
  doi: 10.5281/zenodo.3678927
keywords:
  - "Topic 1"
  - "Topic 2"
date-released: 2021-01-01
license: "CC-BY-4.0"
cff-version: 1.2.0
message: "When citing this dataset, please include both the data citation and the citation for the report component from which the figure originates."
```

## Note for CMIP and CORDEX data analysis

If the figure data is generated from CMIP or CORDEX data, please include in this directory a file named `pids.txt` 
listing (one per line) the PIDs (persistent identifiers) of the datasets used. You can find those under the 
`tracking_id` global attributes of NetCDF files. This will help the TSU track the use of CMIP data in the AR7 
and give credit to data producers.



