
# Pet PyUnify Sample Data Documentation

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
|    | Key         | Value                                                                               |
|---:|:------------|:------------------------------------------------------------------------------------|
|  0 | description | This is a sample dataset of Pets to test PyUnify functionality                      |
|  1 | authors     | Ron Itelman, Cameron Prybol, Stephanie Bankes                                       |
|  2 | contact     | ron@intelligence.ai                                                                 |
|  3 | contract    | https://github.com/JSON-UNIFY                                                       |
|  4 | id          | 1                                                                                   |
|  5 | name        | Pet PyUnify Data Object                                                             |
|  6 | markdown    | https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD |
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
        "name": "Pet PyUnify Data Object",
        "markdown": "https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD"
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
'{"concepts": {"headers": {"name": ["Animal", "Size", "Safe As Pet"], "type": [null, null, null], "description": [null, null, null], "wikidata": [null, null, null]}, "values": {}}, "compute": {"function": [], "event listener description": []}, "custom": {}, "data": {"Animal": ["Mouse", "Cat", "Dog", "Horse", "Lion"], "Size": ["Tiny", "Small", "Medium", "Very Large", "Large"], "Safe As Pet": [false, true, true, true, false]}, "governance": {"sla": {"NAME": [], "TYPE": [], "DESCRIPTION": [], "REQUIREMENTS": []}}, "lineage": {}, "meta": {"description": "This is a sample dataset of Pets to test PyUnify functionality", "authors": "Ron Itelman, Cameron Prybol, Stephanie Bankes", "contact": "ron@intelligence.ai", "contract": "https://github.com/JSON-UNIFY", "id": "1", "name": "Pet PyUnify Data Object", "markdown": "https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD"}, "project": {"description": [], "status": [], "date": []}}'
```
