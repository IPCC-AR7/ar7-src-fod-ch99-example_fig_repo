# Example of a repository for a figure creation script 

Please name your repository according to the following convention:  ``ar7-<report>-<draft>-<chapter>-<figure>``, 
referring to the table below for the abbreviations. 

| Type        | Full name                                | Abbreviation |
|-------------|------------------------------------------|-------------|
| ``report``  |                                          |             |  
|             | Special Report on Cities                 | src         |
|             | Working Group I                          | wg1         |
|             | Working Group II                         | wg2         |
|             | Working Group III                        | wg3         |
|             | Synthesis Report                         | syr         |
| ``draft``   |                                          |             |
|             | First Order Draft                        | fod         |
|             | Second Order Draft                       | sod         |
|             | Final Government Draft                   | fgd         |
| ``chapter`` |                                          |             |
|             | Summary for Policymakers                 | spm         |
|             | Technical Summary                        | ts          |
|             | Chapter 1                                | ch1         |
|             | Cross-Chapter Paper 1                    | ccp1        |
|             | Annex III                                | ann3        |
|             | Atlas                                    | atlas       |
| ``figure``  |                                          |             |
|             | Figure 4.1                               | fig1        |
|             | Cross-Chapter Box 4.1, Figure 1          | ccb1fig1  |
|             | Cross-Section Box TS.1, Figure 1         | csb1fig1  |
|             | Box 4.1, Figure 1                        | box1fig1  |
|             | Frequently Asked Questions 4.1, Figure 1 | faq1fig1  |

Note that this means that we expect authors to create a new repo for each draft. This may feel like a bad practice for 
Git users, but keeping the same repository name across drafts would lead to name conflicts, because figure numbers 
change from one draft to the next. If you don't know yet the draft figure number, enter a descriptive name in the 
``figure`` field, e.g. ``cmip7-sea-ice-extent``, and change the repo name once you know your figure's number. 

For the first order draft (FOD), please minimally include the following content in the repo:

- [ ] A metadata file (`info.yml`) indicating the figure title, authors, the figure caption and the software used (e.g. Excel, Python, R, QGIS);
- [ ] The figure itself in PNG format (`ar7-<report>-<draft>-<chapter>-<figure>.v1.0.png`);

For the second order draft, please include the additional information: 
- [ ] The list of datasets used in the figure, to be included in `info.yml` file (see example below). At 
  this point, specifying a `DOI` is not strictly necessary.   

For the final government draft, please include the following additional content:
- [ ] A figure generation script, e.g. `fig.py` or `fig.R`. If instead the figure was created using a graphical user 
  interface (e.g. ArcGIS), please include detailed instructions in this README on how to reproduce the figure;  
- [ ] A list of the packages and their version necessary to run the script (`requirements.txt`);
- [ ] A `data/` directory including one subdirectory for each dataset displayed in the figure;
- [ ] A `data/README.md` file explaining how to download the data and populate the `data/` directory. If possible, 
  automate the process using a script, e.g. `download.py` or `download.R` that can be run from the command line;
- [ ] A DOI for each dataset listed in `info.yml`;
- [ ] The name of the figure generation script in `info.yml.`

Please do not include add the datasets to this repo. People who want to reproduce the figure are expected to fetch the 
datasets themselves and store them in the `data/` directory according to instructions provided in the `data/README.md` 
file. This is intended to keep a clear distinction between data and code, and facilitate their curation according to best 
practices for data and code.

## Example `info.yml` file

The file ``info.yml`` holds information about the figure, who created it, how and using what datasets.

```yaml
title: Title of figure, e.g. Figure 4.11 | Multiple lines of evidence for global surface air temperature (GSAT) changes for the long-term period, 2081–2100, relative to the average over 1995–2014, for all five priority scenarios.
caption: Standalone description of methods necessary to understand the figure.
filename: ar7-src-fgd-ch5-fig2.v1.0.png
authors:
  - name: Alice Asselin
    orcid: 0000-0000-0000-0000
  - name: Bob Brun
    orcid: 0000-0000-0000-0001
software: Excel
datasets:
  - name: Historical CO2 Record from the Vostok Ice Core
    path: data/vostok-ice-core
    doi: https://doi.org/10.5281/zenodo.3678927
script: fig.py
```

Note that with every pull request into the `main` branch, actions are run to check the conformity of the repo's structure and content. 

Replace the content from this README with something like:

```
# <Figure title>

High level overview of what the figure presents. 

## How to reproduce the figure

- Fetch data following instructions in `data/README.md`;
- Install requirements by running `pip install -r requirements.txt`;
- Run the script `fig.py`.
```
