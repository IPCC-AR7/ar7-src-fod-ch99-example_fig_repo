# IPCC figure submission and curation template

This repository is a template designed to submit figures for IPCC AR7 reports. It defines a directory structure, 
workflows and branch rules to review and validate content. On releases, it creates two Zenodo depositions, one for the 
figure, metadata and figure-generation code, and another for the underlying figure data. 

To use this template ... TODO


Check the [documentation](https://ipcc-ar7.github.io/ipcc-author-guidance/) for submitting figure and data to your TSU.

## Name your repository

Please name your repository according to the following convention:  ``ar7-<report>-<draft>-<chapter>-<figure>``, 
referring to the table below for the abbreviations. 

Note that we expect authors to create a new repo for each draft. This may feel like a bad practice for 
Git users, but keeping the same repository name across drafts would lead to name conflicts, because figure numbers 
change from one draft to the next. If you don't know yet the draft figure number, enter a descriptive name in the 
``figure`` field, e.g. ``cmip7_sea_ice_extent``, and change the repo name once you know your figure's number. 

## Repository content and submission timeline 

This repository is meant to store one IPCC report figure, along with the data and code necessary to reproduce it. We know that publishing 
clean code and data is time-consuming, and that most figures don't survive the rounds of reviews, so we're only expecting 
code and data to be prepared for the Final Government Draft (FGD), not the First Order Draft (FOD) or Second Order Draft (SOD).
However, we also know that delaying the data and code preparation process at the last minute will be painful for everyone 
involved, because it will pile on the final publication rush. What we're proposing is a gradual approach to data and code 
curation, where each draft adds a bit more content to the repository for the sake of building experience and resolving 
issues in a stress-free environment.

### Key concepts

- By *data*, we mean here the data displayed in the figure, not the source datasets they derive from. Please do not commit large input datasets in this repository; 
- By *metadata*, we mean the information about the figure, such as its title, caption, authors, and references. This information is captured in a `CITATION.cff` file, documented [here](https://citation-file-format.github.io/). 

### First Order Draft

For the first order draft (FOD), include the following content:

- [ ] The figure itself in PNG format (e.g. `ar7-<report>-<draft>-<chapter>-<figure>.v1.0.png`);
- [ ] A metadata file (`CITATION.cff`) indicating the figure title, abstract and authors. This repo already includes an example of a `CITATION.cff` file, just fill-in the fields `title`, `abstract` and `authors` and leave the `cff-version` and `message` fields as-is.

### Second Order Draft

For the second order draft (SOD), please include additional information: 

- [ ] A draft version of the data underlying the figure in the `data/` directory;
- [ ] A metadata file `data/CITATION.cff`) indicating the data title, authors and references to source data and papers; 
- [ ] A draft version of the code generating the figure from the data; 
- [ ] A reference to the data in the `CITATION.cff` file in the `references` field.

### Final Government Draft

This is the last draft, and the content of the repository will be archived and made publicly available at the report's publication. It's 
important to complete the metadata and make sure the figure creation script works because the TSU might have to make small edits to 
figures *live* during the government review. 

For the final government draft, please include the following additional content:
- [ ] A figure generation script named `fig.*`, e.g. `fig.py` or `fig.R`. If instead the figure was created using a graphical user 
  interface (e.g. ArcGIS), please include detailed instructions in this README on how to reproduce the figure;  
- [ ] A list of the packages and their version necessary to run the script (`requirements.txt`);
- [ ] A `data/README.md` file explaining how to download the data and populate the `data/` directory. If possible, 
  automate the process using a script, e.g. `download.py` or `download.R` that can be run from the command line;
- [ ] A DOI for each reference listed in `CITATION.cff` and `/data/CITATION.cff` (e.g. just `10.5281/zenodo.3678927`, without the `http://doi.org/`).


## Creating releases

To submit a figure to the TSU, create a *release*. Go the `Code` page on Github, click on `Create a new release`, enter a tag following the 
convention `vX.Y.Z`, where `X` is 0, 1, 2, 3 for ZOD, FOD, SOD and FGD respectively, `Y` is the figure version number, and `Z` 
the *patch* number. Change `Y` is the figure changes substantially (for example the addition of a new element), and change `Z` 
for minor edits (colors, marker size, typos, etc). Enter the same tag as the *Release title*, click on *Generate release notes* 
to fill in the description, edit as needed and press *Publish release*. 

TODO: Zenodo follow-up

## The `CITATION.cff` file

The file ``CITATION.cff`` holds information about the figure, who created it, how and using what reference datasets or papers. It minimally requires a `title`, `authors`, `message` and the `cff-version`. TSUs impose additional requirements depending on the draft order:

- FOD: `abstract` with the figure caption;
- SOD: `references` with the list of references (data and/or publication) used to create the figure;
- FGD: a `doi` for each reference listed in the `references` field.  

### Authors

TODO: How to fill authors field (person or entity)
Note that Zenodo storage will fail if invalid author ORCID are provided.

### References

TODO: How to fill references field.

### Example of a `CITATION.cff` file

```yaml
title: Title of figure, e.g. Figure 4.11 | Multiple lines of evidence for global surface air temperature (GSAT) changes for the long-term period, 2081–2100, relative to the average over 1995–2014, for all five priority scenarios.
abstract: Standalone description of methods necessary to understand the figure.
authors:
  - family-names: Asselin
    given-names: Alice
    orcid: "https://orcid.org/0000-0000-0000-0001"
  - family-names: Brun
    given-names: Bob
    orcid: "https://orcid.org/0000-0000-0000-0001"
references:
  - title: Data for Figure 4.11 of AR7 SRC Chapter 4
    authors:
      - name: A. Asselin et al.
    type: data
    data-type: CSV
    doi: 10.5281/zenodo.3678927
cff-version: 1.2.0
```

## Controlled vocabulary

Whenever a template includes fields for `<report>, <draft>, <chapter>` or `<figure>`, please use abbreviations from the table below.

| Type        | Full name                                 | Abbreviation |
|-------------|-------------------------------------------|-------------|
| ``report``  |                                           |             |  
|             | Special Report on Cities                  | src         |
|             | Working Group I                           | wg1         |
|             | Working Group II                          | wg2         |
|             | Working Group III                         | wg3         |
|             | Synthesis Report                          | syr         |
| ``draft``   |                                           |             |
|             | Zero Order Draft                          | zod         | 
|             | First Order Draft                         | fod         |
|             | Second Order Draft                        | sod         |
|             | Final Government Draft                    | fgd         |
| ``chapter`` |                                           |             |
|             | Summary for Policymakers                  | spm         |
|             | Technical Summary                         | ts          |
|             | Chapter 1                                 | ch1         |
|             | Cross-Chapter Paper 1                     | ccp1        |
|             | Annex III                                 | ann3        |
|             | Atlas                                     | atlas       |
| ``figure``  |                                           |             |
|             | Figure 4.1                                | fig1        |
|             | Cross-Chapter Box 4.1, Figure 1           | ccb1fig1  |
|             | Cross-Section Box TS.1, Figure 1          | csb1fig1  |
|             | Box 4.1, Figure 1                         | box1fig1  |
|             | Frequently Asked Questions 4.1, Figure 1  | faq1fig1  |

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

## For developers

To fetch a Zenodo record: 
```bash
curl https://sandbox.zenodo.org/api/records/<record id>?access_token=<access token> -H 'accept: application/vnd.zenodo.v1+json'
```
Other output formats are available. Use DataCite to extract translated titles and descriptions.
