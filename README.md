# Example of a repository for an IPCC figure

Please name your repository according to the following convention:  ``ar7-<report>-<draft>-<chapter>-<figure>``, 
referring to the table below for the abbreviations. 

Note that we expect authors to create a new repo for each draft. This may feel like a bad practice for 
Git users, but keeping the same repository name across drafts would lead to name conflicts, because figure numbers 
change from one draft to the next. If you don't know yet the draft figure number, enter a descriptive name in the 
``figure`` field, e.g. ``cmip7_sea_ice_extent``, and change the repo name once you know your figure's number. 

## Repository content

The content that TSUs expect is minimal for the First Order Draft, and grows gradually as we near the Final Government Draft. 

### First Order Draft

For the first order draft (FOD), include the following content:

- [ ] A metadata file (`CITATION.cff`) indicating the figure title, authors, the figure caption and the software used (e.g. Excel, Python, R, QGIS);
- [ ] The figure itself in PNG format (e.g. `ar7-<report>-<draft>-<chapter>-<figure>.v1.0.png`);

### Second Order Draft

For the second order draft (SOD), please include the additional information: 

- [ ] The list of datasets used in the figure, to be included in `CITATION.cff` file (see example below). At 
  this point, specifying a `DOI` is not strictly necessary.   

### Final Government Draft

This is the last draft, and the content of the repository will be archived and made publicly available at the report's publication. It's 
important to complete the metadata and make sure the figure creation script works because the TSU might have to make small edits to 
figures *live* during the government review. 

For the final government draft, please include the following additional content:
- [ ] A figure generation script, e.g. `fig.py` or `fig.R`. If instead the figure was created using a graphical user 
  interface (e.g. ArcGIS), please include detailed instructions in this README on how to reproduce the figure;  
- [ ] A list of the packages and their version necessary to run the script (`requirements.txt`);
- [ ] A `data/` directory including one subdirectory for each dataset displayed in the figure;
- [ ] A `data/README.md` file explaining how to download the data and populate the `data/` directory. If possible, 
  automate the process using a script, e.g. `download.py` or `download.R` that can be run from the command line;
- [ ] A DOI for each dataset listed in `CITATION.cff`;

Please do not include the datasets in this repo. People who want to reproduce the figure are expected to fetch the 
datasets themselves and store them in the `data/` directory, according to instructions provided in the `data/README.md` 
file. This is intended to keep a clear distinction between data and code, and facilitate their curation according to best 
practices for each.

## Creating releases

To submit a figure to the TSU, create a *release*. Go the `Code` page on Github, click on `Create a new release`, enter a tag following the 
convention `vX.Y.Z`, where `X` is 0, 1, 2, 3 for ZOD, FOD, SOD and FGD respectively, `Y` is the figure version number, and `Z` 
the *patch* number. Change `Y` is the figure changes substantially (for example the addition of a new element), and change `Z` 
for minor edits (colors, marker size, typos, etc). Enter the same tag as the *Release title*, click on *Generate release notes* 
to fill in the description, edit as needed and press *Publish release*. 

## Example `CITATION.cff` file

The file ``CITATION.cff`` holds information about the figure, who created it, how and using what reference datasets or papers.

```yaml
title: Title of figure, e.g. Figure 4.11 | Multiple lines of evidence for global surface air temperature (GSAT) changes for the long-term period, 2081–2100, relative to the average over 1995–2014, for all five priority scenarios.
abstract: Standalone description of methods necessary to understand the figure.
authors:
  - orcid: "https://orcid.org/0000-0000-0000-0001"
    given-names: Alice
    family-names: Asselin
  - orcid: "https://orcid.org/0000-0000-0000-0001"
    given-names: Bob
    family-names: Brun
keywords:
  - "ice cores"
  - CO2
references:
  - title: Historical CO2 Record from the Vostok Ice Core
  - authors:
      - name: J.M. Barnola et al.
    type: data
    data-type: CSV
    filename: data/vostok-ice-core/vostok.icecore.co2
    doi: 10.5281/zenodo.3678927
license: CC0-1.0
cff-version: 1.2.0
```

## Controlled vocabulary

Whenever a template includes fields for `<report>, <draft>, <chapter>` or `<figure>`, please use abbreviations from the table below.

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

Note that with every pull request into the `main` branch, actions are run to check the conformity of the repo's structure and content. 

## Last steps

Replace the content from this README with something like:

```
# <Figure title>

High level overview of what the figure presents. 

## How to reproduce the figure

- Fetch data following instructions in `data/README.md`;
- Install requirements by running `pip install -r requirements.txt`;
- Run the script `fig.py`.
```
