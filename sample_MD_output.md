# Auto-generate JSON-Unify documentation with PyUnify


### THE SPECIFICATION

    JSON-Unify = {
      concepts: {}
      data: {},
      meta: {}
    }
    

JSON-Unify is a simple specification requiring **metadata**, **concepts**, and **data** are in one self-contained JSON object.
There are **recommendedations** to further enrich your data in the specification, but they are not requirements. You can view those at: https://github.com/JSON-UNIFY 
PyUnify is a Python library that auto-generates and adds recommended JSON-Unify properties. For example, 'meta' recommended fields are:
      {
        "contract":"https://github.com/JSON-UNIFY",
        "description": None,
        "source": None,
        "table": None,
        "query": None,
        "tags": None,
        "authors": None,
        "id": None,
        "contact": None,
        "name": None
    }

    
The purpose and benefit of using JSON-Unify is to improve the user experience of those who create, consume, and share data by reducing ambiguitiy and saving time.


You can have a pointer (URL reference) to the data if the data is large or if the data is not in JSON format. This still provides a single object in JSON format that can be used to communicate dataTo instantiate this JSON-Unify data contract with PyUnify:
- Copy the JSON code in this MD file below.
- In your Python Notebook:
```
import pyunify
unify = PyUnify(paste_json_here)
```

This markdown file was automatically generated with 
```
unify.md()
```

To edit the title of the documentation use: 
```
unify.md({'title':'My title here'})
```

Otherwise, the title will be auto-generated from the meta name property## Concepts - Headers

```
|    | name               | type   | description   | wikidata   |
|---:|:-------------------|:-------|:--------------|:-----------|
|  0 | ID                 |        |               |            |
|  1 | First name         |        |               |            |
|  2 | Last name          |        |               |            |
|  3 | Birth year         |        |               |            |
|  4 | Height             |        |               |            |
|  5 | Birthplace         |        |               |            |
|  6 | Identity is secret |        |               |            |
|  7 | Can fly            |        |               |            |
|  8 | Alignment          |        |               |            |
|  9 | Wears cape         |        |               |            |
```
## Concepts - Values

```

```
## Data

```
|    |   ID | First name   | Last name   | Birth year   | Height   | Birthplace      | Identity is secret   | Can fly   | Alignment    | Wears cape   |
|---:|-----:|:-------------|:------------|:-------------|:---------|:----------------|:---------------------|:----------|:-------------|:-------------|
|  1 | 7435 | Bruce        | Wayne       | 1969*        | 6'2"     | Gotham          | Y                    | 3         | anti-villain | black        |
|  2 | 0958 | Ororo        | Munroe      | --1979--     | 5'11"    | Manhattan       |                      | 9         | good         | long         |
|  3 | 9471 | Diana        | Trevor      | 1618         | 5'8"     | Paradise Island | Y                    | Jet       | truth        | rarely       |
|  4 | 9483 | Janet        | Van Dyne    | 19.42        | 5'4"     | Cresskill       |                      | tiny      | Good         | Not really   |
|  5 | 0696 | Peter        | Parker      | 11111983     | 5'10"    | Queens          | Y                    | Fall      | right        | never        |
|  6 | 5531 | Harleen      | Quinzell    | 1981         | 6'0"     | Gotham          | Y                    |           | evil         | no           |
|  7 | 4734 | Erik         | Lehnsherr   | 1-9-8-3      | 5'7"     | Hamburg         |                      | Lev.      | mutants      | Absolutely   |
|  8 | 7757 | Natasha      | Romanova    | 1983         | 5'6"     | St. Petersburg  |                      | jet       | depends      | No way       |
|  9 | 0323 | Jean         | Grey        | "1977"       | 6'4"     | Annandale       |                      | No        | good         | Mostly not   |
| 10 | 3980 | Clark        | Kent        | "1954"       | 6'2"     | Krypton         | Y                    | 12        | Truth        | always       |
| 11 | 3057 | Victor       | Von Doom    | "1943"       | 6'2"     | Latveria        |                      | 1         | Bad          | yes          |
| 12 | 0573 | Stephen      | Strange     | 1968         | 6'2"     | Philidelphia    |                      | not       | light        | T            |
| 13 | 7452 | Thor         | Odinson     | 2287 BC      | 6'6"     | Norway          |                      | 10        | Good         | Of course    |
| 14 | 1437 | Selina       | Kyle        | 1998         | 5'7"     | Gotham          | Y                    | NA        | Neutral      | It clashes   |
| 15 | 1883 | Raven        | Darkholme   | ..1911..     | 5'10"    | unknown         | Y                    | no        | mostly bad   | Not really   |
| 16 | 5830 | Kara         | Zor-el      | 1961         | 5'7"     | Krypton         | Y                    | fast      | G            | yes          |
```
## Meta

```
|    | Key         | Value                         |
|---:|:------------|:------------------------------|
|  0 | contract    | https://github.com/JSON-UNIFY |
|  1 | description |                               |
|  2 | source      |                               |
|  3 | table       |                               |
|  4 | query       |                               |
|  5 | tags        |                               |
|  6 | authors     |                               |
|  7 | id          |                               |
|  8 | contact     |                               |
|  9 | name        |                               |
```
## Governance - SLA

```
|    | Key         | Value                         |
|---:|:------------|:------------------------------|
|  0 | contract    | https://github.com/JSON-UNIFY |
|  1 | description |                               |
|  2 | source      |                               |
|  3 | table       |                               |
|  4 | query       |                               |
|  5 | tags        |                               |
|  6 | authors     |                               |
|  7 | id          |                               |
|  8 | contact     |                               |
|  9 | name        |                               |
```
