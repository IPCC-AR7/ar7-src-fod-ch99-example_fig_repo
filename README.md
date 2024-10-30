# Example of a repository for a figure creation script 

Repository naming convention:  ``ar7-<report>-<draft>-<chapter>-fig<figure #>``
Consult the [documentation](https://ipcc-ar7.github.io/ipcc-author-guidance/) for the terms allowed for the different placeholders (`<report>, <draft>, <chapter>`)


For the first order draft (FOD), please minimally include the following content:

- [ ] A metadata file (`figure.yml`) indicating the figure title, authors, the figure caption and the software used (e.g. Excel, Python, R, QGIS);
- [ ] The figure itself in PNG format (`ar7-<report>-<chapter>-fig<#>.v1.0.0.png`);

For the second order draft (SOD), please include the additional information: 
- [ ] If Python or R are used as the software, include a figure generation script named `fig.py` or `fig.R`.
- [ ] Include a list of the packages and their version necessary to run the script in a file called `requirements.txt`
- [ ] A `data/` directory holding a metadata file (`data/data.yml`) indicating references to data displayed in the figure.
- [ ] A `data/README.md` file explaining how to download the data and populate the `data/` directory. If possible, automate the process using a script, e.g. `download.py` or `download.R` that can be run from the command line. 

Note that with every pull request into the `main` branch, actions are run to check the conformity of the repo's structure and content. 

Replace the content from this README with 

```
# <Figure title>

High level overview of what the figure presents. 
```



