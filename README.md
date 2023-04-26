[![Python application](https://github.com/jermwatt/pypmed/actions/workflows/python-app.yml/badge.svg)](https://github.com/jermwatt/pypmed/actions/workflows/python-app.yml)

# pypmed - a simple Python interface for [PubMed's API](https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi/)

pypmed is a Python library that provides easy access to the [PubMed's APIs](https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi/).

## Installation

`pip install pypmed`

## Example usage

This example can be executed in [this example notebook](https://colab.research.google.com/github/jermwatt/pynih/blob/main/pynih_example_usage.ipynb#scrollTo=mTC2IDzs7_l1).

```python
from pynih import apis

# illustration of project api usage
search_criteria = {'appl_id':'9795459'}
include_fields = ['ApplId', 'ProjectTitle']
project_data = apis.query_project_api(include_fields=include_fields, search_criteria=search_criteria)

# illustration of publication api usage
search_criteria = {'pmid':'26657764'}
publication_data = apis.query_publication_api(search_criteria=search_criteria)
```

### `query_project_api` input parameters

The project API `query_project_api` has the following input parameters:

`search_criteria` - query search criteria.  Example: `{"use_relevance": True, "fiscal_years": [2023],"include_active_projects": True}`

`include_fields` - fields to include in return payload.   Example: The output result payload would have only ten fields/columns: "include_fields": `[ "ApplId","SubprojectId","FiscalYear","OrgName","OrgCity", "OrgState","OrgStateName","DeptType", "ProjectNum","OrgCountry" ]`.  Default value: all.

`limit` - number of entries to return (maximum 500 per query).  Default value: 1.

`offset` - Starting counter for return items (projects). Default value: 0.  Maximum allowable value: 14,999 or length of records.

See [official documentation](https://api.reporter.nih.gov/#/Search/post_v2_projects_search) for further information on these inputs.


## Notice of Non-Affiliation and Disclaimer 
The author of this library is not affiliated, associated, authorized, endorsed by, or in any way officially connected with the NIH, or any of its subsidiaries or its affiliates. The official NIH Reporter website can be found at https://reporter.nih.gov/
