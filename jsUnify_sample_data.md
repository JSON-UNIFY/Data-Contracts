## Concepts - Headers
Any documentation or the concepts used in the headers of your data table.
```
|    | name             | type   | description                                                 |
|---:|:-----------------|:-------|:------------------------------------------------------------|
|  0 | Animal           | string | The name of the animal                                      |
|  1 | Size             | string | The size of the animal                                      |
|  2 | Gender           | string | The gender of the animal used in the weight and size fields |
|  3 | Safe As Pet      | bool   | Whether the animal is safe to have as a pet                 |
|  4 | Weight In Pounds | float  | The average weight of the animal                            |
```
## Concepts - Values
Any documentation or the concepts used in the values of a column in your data table.
```
| entity   | header name   | type   | description   |
|----------|---------------|--------|---------------|
```
## Concepts - Features
Any documentation or the concepts used in the features of a column in your data table.
```
| entity   | header name   | type   | description   |
|----------|---------------|--------|---------------|
```
## Meta
Any documentation of the metadata used to describe and discover your data.
```
|    | key           | value                                                                               |
|---:|:--------------|:------------------------------------------------------------------------------------|
|  0 | contract      |                                                                                     |
|  1 | description   | This is a sample dataset of Pets to test PyUnify functionality                      |
|  2 | authors       | Ron Itelman, Cameron Prybol, Stephanie Bankes                                       |
|  3 | contact       | ron@intelligence.ai                                                                 |
|  4 | specification | https://github.com/JSON-UNIFY                                                       |
|  5 | id            | 1                                                                                   |
|  6 | name          |                                                                                     |
|  7 | markdown      | https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD |
```
## Governance - SLA
Any documentation of any SLA information.
```
| category   | provider   | customer   | requirement   |
|------------|------------|------------|---------------|
```
## Lineage
Data lineage information
```
|    | command                      | params                                                                                                                                                                                                      | date                       |
|---:|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------|
|  0 | pyunify object initilization |                                                                                                                                                                                                             | 2022-12-08 04:57:16.948474 |
|  1 | unify.query()                | headers update [{'row': 1, 'col': 'description', 'set': 'The size of the animal'}, {'row': 2, 'col': 'type', 'set': 'string'}]                                                                              | 2022-12-08 04:57:16.948614 |
|  2 | unify.query()                | requirements insert [{'minimum': '', 'exclusiveMinimum': '', 'maximum': '', 'exclusiveMaximum': '', 'options': 'Tiny, Small, Medium, Very Large, Large', 'options_default_selected': '', 'header': 'Size'}] | 2022-12-08 04:57:16.948735 |
```
## Data
The data of your JSON-Unify object.
```
|    | Animal   | Size       | Gender   | Safe As Pet   |   Weight In Pounds |
|---:|:---------|:-----------|:---------|:--------------|-------------------:|
|  0 | Mouse    | Tiny       | Female   | True          |                0.5 |
|  1 | Cat      | Small      | Female   | True          |                9   |
|  2 | Dog      | Medium     | Male     | True          |              100   |
|  3 | Horse    | Very Large | Female   | True          |              930   |
|  4 | Lion     | Large      | Male     | False         |              420   |
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
                "Gender",
                "Safe As Pet",
                "Weight In Pounds"
            ],
            "type": [
                "string",
                "string",
                "string",
                "bool",
                "float"
            ],
            "description": [
                "The name of the animal",
                "The size of the animal",
                "The gender of the animal used in the weight and size fields",
                "Whether the animal is safe to have as a pet",
                "The average weight of the animal"
            ]
        },
        "values": {
            "entity": [],
            "header name": [],
            "type": [],
            "description": []
        },
        "features": {
            "row": [],
            "column": [],
            "table": [],
            "relation": [],
            "description": []
        }
    },
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
        "Gender": [
            "Female",
            "Female",
            "Male",
            "Female",
            "Male"
        ],
        "Safe As Pet": [
            true,
            true,
            true,
            true,
            false
        ],
        "Weight In Pounds": [
            0.5,
            9,
            100,
            930,
            420
        ]
    },
    "governance": {
        "sla": {
            "category": [],
            "provider": [],
            "customer": [],
            "requirement": []
        },
        "requirements": {
            "header": [
                "Size"
            ],
            "minimum": [
                ""
            ],
            "exclusiveMinimum": [
                ""
            ],
            "maximum": [
                ""
            ],
            "exclusiveMaximum": [
                ""
            ],
            "options": [
                "Tiny, Small, Medium, Very Large, Large"
            ],
            "options_default_selected": [
                ""
            ]
        }
    },
    "lineage": {
        "command": [
            "pyunify object initilization",
            "unify.query()",
            "unify.query()",
            "Markdown file created"
        ],
        "params": [
            null,
            "headers update [{'row': 1, 'col': 'description', 'set': 'The size of the animal'}, {'row': 2, 'col': 'type', 'set': 'string'}]",
            "requirements insert [{'minimum': '', 'exclusiveMinimum': '', 'maximum': '', 'exclusiveMaximum': '', 'options': 'Tiny, Small, Medium, Very Large, Large', 'options_default_selected': '', 'header': 'Size'}]",
            null
        ],
        "date": [
            "2022-12-08 04:57:16.948474",
            "2022-12-08 04:57:16.948614",
            "2022-12-08 04:57:16.948735",
            "2022-12-08 04:57:17.099380"
        ]
    },
    "schema": {
        "$schema": "https://json-schema.org/draft/2020-12/schema",
        "$id": null,
        "title": null,
        "description": null,
        "type": "object",
        "properties": {}
    },
    "json-ld": [],
    "meta": {
        "key": [
            "contract",
            "description",
            "authors",
            "contact",
            "specification",
            "id",
            "name",
            "markdown"
        ],
        "value": [
            null,
            "This is a sample dataset of Pets to test PyUnify functionality",
            "Ron Itelman, Cameron Prybol, Stephanie Bankes",
            "ron@intelligence.ai",
            "https://github.com/JSON-UNIFY",
            "1",
            null,
            "https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD"
        ]
    }
}
```
## JSON-Unify Object (string)
Use this version to copy and paste into Jupyter Notebook to create a PyUnify Object


```
'{"concepts": {"headers": {"name": ["Animal", "Size", "Gender", "Safe As Pet", "Weight In Pounds"], "type": ["string", "string", "string", "bool", "float"], "description": ["The name of the animal", "The size of the animal", "The gender of the animal used in the weight and size fields", "Whether the animal is safe to have as a pet", "The average weight of the animal"]}, "values": {"entity": [], "header name": [], "type": [], "description": []}, "features": {"row": [], "column": [], "table": [], "relation": [], "description": []}}, "data": {"Animal": ["Mouse", "Cat", "Dog", "Horse", "Lion"], "Size": ["Tiny", "Small", "Medium", "Very Large", "Large"], "Gender": ["Female", "Female", "Male", "Female", "Male"], "Safe As Pet": [true, true, true, true, false], "Weight In Pounds": [0.5, 9, 100, 930, 420]}, "governance": {"sla": {"category": [], "provider": [], "customer": [], "requirement": []}, "requirements": {"header": ["Size"], "minimum": [""], "exclusiveMinimum": [""], "maximum": [""], "exclusiveMaximum": [""], "options": ["Tiny, Small, Medium, Very Large, Large"], "options_default_selected": [""]}}, "lineage": {"command": ["pyunify object initilization", "unify.query()", "unify.query()", "Markdown file created"], "params": [null, "headers update [{\'row\': 1, \'col\': \'description\', \'set\': \'The size of the animal\'}, {\'row\': 2, \'col\': \'type\', \'set\': \'string\'}]", "requirements insert [{\'minimum\': \'\', \'exclusiveMinimum\': \'\', \'maximum\': \'\', \'exclusiveMaximum\': \'\', \'options\': \'Tiny, Small, Medium, Very Large, Large\', \'options_default_selected\': \'\', \'header\': \'Size\'}]", null], "date": ["2022-12-08 04:57:16.948474", "2022-12-08 04:57:16.948614", "2022-12-08 04:57:16.948735", "2022-12-08 04:57:17.099380"]}, "schema": {"$schema": "https://json-schema.org/draft/2020-12/schema", "$id": null, "title": null, "description": null, "type": "object", "properties": {}}, "json-ld": [], "meta": {"key": ["contract", "description", "authors", "contact", "specification", "id", "name", "markdown"], "value": [null, "This is a sample dataset of Pets to test PyUnify functionality", "Ron Itelman, Cameron Prybol, Stephanie Bankes", "ron@intelligence.ai", "https://github.com/JSON-UNIFY", "1", null, "https://github.com/JSON-UNIFY/Data-Contracts/blob/main/1_Pet_PyUnify_Sample_Data.MD"]}}'
```
