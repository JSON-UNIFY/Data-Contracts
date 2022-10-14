# json-unify
Open Source Data Contracts 

### Simply, a data contract is a declarative agreement between a sender and receiver of information in a communication event (API payload for example).
### A data contract has a functional purpose of reducing ambiguity and errors, and increasing trust and efficiency.
### The JSON-UNIFY specification has three requirements: @metadata, @data, and @semantics

DESIGNED FOR SIMPLICITY, CONFIGURABILITY, AND SCALABILITY
By making the entire data contract a JSON specification, it has maximum flexibility for customization, including industry-specific templates and standards.

BENEFITS:
Ensure that metadata is included with the data, so that users don't have to waste time trying to understand what a column definition really means.
Allow for any format / data representation (CSV, JSON, Relational Table using SQL, etc.)
Allow for any industry to have 3rd party reference frames for data contracts, for federated computing
Enable sequential / temporal agreements

<img src="https://github.com/Intelligence-AI/json-unify/blob/main/data_contract.png" height="600" />

REQUIRED PAYLOAD PROPERTIES
## @metadata
- @contract - specification for the contract, so receivers and senders have an agreement on the format
- @communication - how the information will be transmitted and received
- @policies - any legal, license, or governance policies associated with the contract

## @data
Depending on the type of data, one or more of these must be included:
- @relational: relational table data (database, table, columns, rows)
- @json: json (object, keys and values)
- @json-ld: any legal, license, or governance policies associated with the contract
- @pandas: the formats used by pandas
- @csv: the formats used by comma separated values (CSV) files
- @rdf: the formats used by RDF

## @semantics
- A semantic reference MUST be included for any table columns and/or JSON keys
- A semantic reference MAY be included for any table row values and/or JSON values

# TEMPLATES

- Relational Tables (Coming soon)
- Graphs (Coming Soon)
- JSON (Below)

## JSON TEMPLATE
### This example is a simple request for cities that a user has visited and rated. 
### Please notice the semantic values use an ontology (optional), but for something custom (rating), the user has defined their own description (required). 


```
{
  "@metadata": {
    "@contract": {
      "uri": "https://github.com/Intelligence-AI/json-unify/blob/main/README.md#json-template",
      "id": "1"

    },
    "@communication": {
      "method": "GET",
      "endpoint": "my_site.com/api/25958",
      "protocol": "https"
    },
    "@policies": {
      "license": "The GNU General Public License v3.0",
      "url": "https://www.gnu.org/licenses/gpl-3.0.en.html"
    }
  },
  "@data": {    
    "@json": 
      {        
        "visits": [
          {
            "city": "San Francisco",
            "latitude": 452343.4323,
            "longitude": 39484.343,
            "rating": 5
          },
          {
            "city": "New York",
            "latitude": 234.3423,
            "longitude": 243384.23433,
            "rating": 4
          },
          {
            "city": "San Francisco",
            "latitude": 452343.4323,
            "longitude": 39484.343,
            "rating": 4
          }
        ]
      }    
  },
  "@semantics": {    
    "@json": {
      "@keys": [
        {
          "city": {
            "ontology": "https://babelnet.org/synset?id=bn%3A00019319n&orig=city&lang=EN",
            "definition": "A large and densely populated urban area; may include several independent administrative districts "
          }
        },
        {
          "latitude": {
            "ontology": "https://babelnet.org/synset?id=bn%3A00050177n&orig=latitude&lang=EN",
            "definition": "The angular distance between an imaginary line around a heavenly body parallel to its equator and the equator itself"
          }
        },
        {
          "longitude": {
            "ontology": "https://babelnet.org/synset?id=bn%3A00051951n&orig=longitude&lang=EN",
            "definition": "The angular distance between a point on any meridian and the prime meridian at Greenwich"
          }
        },
        {
          "rating": {
            "ontology": null,
            "definition": "A rating between 1 to 5, where 1 is the worst, 3 is neutral, and 5 is the best"
          }
        }
      ],
      "@values": [
        {
          "San Francisco": {
            "ontology": "https://babelnet.org/synset?id=bn%3A00069104n&orig=San%20Francisco&lang=EN",
            "definition": "A port in western California near the Golden Gate that is one of the major industrial and transportation centers; it has one of the world's finest harbors; site of the Golden Gate Bridge"
          }
        },
        {
          "New York": {
            "ontology": "https://babelnet.org/synset?id=bn%3A00041611n&orig=New%20York&lang=EN",
            "definition": "The largest city in New York State and in the United States; located in southeastern New York at the mouth of the Hudson river; a major financial and cultural center"
          }
        }
      ]
    }
    
  }
}
```
