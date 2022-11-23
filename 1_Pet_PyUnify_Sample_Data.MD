# Auto-generate JSON-Unify documentation with PyUnify


### THE JSON-Unify SPECIFICATION


JSON-Unify is a <em>minimal & simple specification</em> requiring **metadata**, **concepts**, and **data** are in one self-contained JSON object.
```
JSON-Unify = {
	concepts: {},
	data: {},
	meta: {}
}
```

### BENEFITS

No license needed, no technology to budget, buy, or implement. Anyone can use it, an obvious and simple user experience that will help entire teams.
The purpose and benefit of using JSON-Unify is to improve the user experience of those who create, consume, and share data by reducing ambiguitiy and saving time.


### PyUnify IS A WRAPPER TO MAKE WORKING WITH JSON-UNIFY EASY

- PyUnify is a Python library that auto-generates and adds recommended JSON-Unify properties, as well as helper functions like exporting .MD files.
- View the **specification** and **recommendations** to further enrich your data in the specification at: https://github.com/JSON-UNIFY.
- For example, a few 'meta' recommended fields are: a description of the data, the source of the data, the author of the data, the data contract URL.
To instantiate this JSON-Unify data contract with PyUnify:

- Copy the JSON code in this MD file below.
- In your **Python Notebook**:
```
!pip install PyUnify
import PyUnify
unify = PyUnify(paste_json_from_this_MD_file)
```

This markdown file was automatically generated with 
```
unify.md()
```

To edit the title of the documentation use: 
```
unify.md({'title':'My title here'})
```

Otherwise, the title will be auto-generated from the meta name property

## Example PyUnify .MD output when the only input is a data set

### PyUnify can guide you step-by-step to fill out empty tables and fields in order to enrich the discoverability and quality of the data experience you are creating for those that will use your data.
## Concepts - Headers
Any documentation or the concepts used in the headers of your data table.
```
|    | name        | type   | description   | wikidata   |
|---:|:------------|:-------|:--------------|:-----------|
|  0 | Animal      |        |               |            |
|  1 | Size        |        |               |            |
|  2 | Safe As Pet |        |               |            |
```
## Concepts - Values
Any documentation or the concepts used in the values of acolumn in your data table.
```

```
## Data
The data of your JSON-Unify object.
```
|    | Animal   | Size       | Safe As Pet   |
|---:|:---------|:-----------|:--------------|
|  0 | Mouse    | Tiny       | False         |
|  1 | Cat      | Small      | True          |
|  2 | Dog      | Medium     | True          |
|  3 | Horse    | Very Large | True          |
|  4 | Lion     | Large      | False         |
```
## Meta
Any documentation of the metadata used to describe and discover your data.
```
|    | Key         | Value                                                          |
|---:|:------------|:---------------------------------------------------------------|
|  0 | description | This is a sample dataset of Pets to test PyUnify functionality |
|  1 | authors     | Ron Itelman, Cameron Prybol, Stephanie Bankes                  |
|  2 | contact     | ron@intelligence.ai                                            |
|  3 | contract    | https://github.com/JSON-UNIFY                                  |
|  4 | id          | 1                                                              |
|  5 | name        | Pet PyUnify Data Object                                        |
```
## Governance - SLA
Any documentation of any SLA information.
```
| NAME   | TYPE   | DESCRIPTION   | REQUIREMENTS   |
|--------|--------|---------------|----------------|
```

## JSON-Unify Object (file)
This is the JavaScript Object Notation representation of your PyUnify Object. You could save this to a file and import it, use it in Javascript, etc.


```
{
    "concepts": {
        "headers": {
            "name": [
                "Animal",
                "Size",
                "Safe As Pet"
            ],
            "type": [
                null,
                null,
                null
            ],
            "description": [
                null,
                null,
                null
            ],
            "wikidata": [
                null,
                null,
                null
            ]
        },
        "values": {}
    },
    "compute": {
        "function": [],
        "event listener description": []
    },
    "custom": {},
    "data": {
        "Animal": [
            "Mouse",
            "Cat",
            "Dog",
            "Horse",
            "Lion"
        ],
        "Size": [
            "Tiny",
            "Small",
            "Medium",
            "Very Large",
            "Large"
        ],
        "Safe As Pet": [
            false,
            true,
            true,
            true,
            false
        ]
    },
    "governance": {
        "sla": {
            "NAME": [],
            "TYPE": [],
            "DESCRIPTION": [],
            "REQUIREMENTS": []
        }
    },
    "lineage": {},
    "meta": {
        "description": "This is a sample dataset of Pets to test PyUnify functionality",
        "authors": "Ron Itelman, Cameron Prybol, Stephanie Bankes",
        "contact": "ron@intelligence.ai",
        "contract": "https://github.com/JSON-UNIFY",
        "id": "1",
        "name": "Pet PyUnify Data Object"
    },
    "project": {
        "description": [],
        "status": [],
        "date": []
    }
}
```
## JSON-Unify Object (string)
Use this version to copy and paste into Jupyter Notebook to create a PyUnify Object


```
'{"concepts": {"headers": {"name": ["Animal", "Size", "Safe As Pet"], "type": [null, null, null], "description": [null, null, null], "wikidata": [null, null, null]}, "values": {}}, "compute": {"function": [], "event listener description": []}, "custom": {}, "data": {"Animal": ["Mouse", "Cat", "Dog", "Horse", "Lion"], "Size": ["Tiny", "Small", "Medium", "Very Large", "Large"], "Safe As Pet": [false, true, true, true, false]}, "governance": {"sla": {"NAME": [], "TYPE": [], "DESCRIPTION": [], "REQUIREMENTS": []}}, "lineage": {}, "meta": {"description": "This is a sample dataset of Pets to test PyUnify functionality", "authors": "Ron Itelman, Cameron Prybol, Stephanie Bankes", "contact": "ron@intelligence.ai", "contract": "https://github.com/JSON-UNIFY", "id": "1", "name": "Pet PyUnify Data Object"}, "project": {"description": [], "status": [], "date": []}}'
```
