# JSON-Unify is an Open-Source Data Contract Specification 
A simple specification for open-source data contracts to unify agreement, understanding, and expectations

### The purpose of JSON-Unify is to unite the data, concept/semantic information, metadata, lineage, governance, etc. into one singular object, thereby eliminating common sources of ambiguity and time-wasted in wanting to understand and use data.

### The only requirement for a JSON-Unify object is that "meta", "concepts", and "data" are all in one object. If the data is large, a link to the data under meta.source (JS) or "meta"["source"] (Python) is allowed.

### Recommended JSON-Unify structure:

```
let json = {
    concepts: {
      headers: {
        name:[],
        type:[],
        description:[]
      },
      values: {
        entity:[],
        header:[],
        type:[],
        description:[]
      },
      features: {
        row:[],
        column:[],
        feature:[],
        relation:[]
      }
    },
    data: {},
    meta: {
      key:["specification", "description", "source", "authors", "contact", "name", "markdown"],
      value: ["https://github.com/JSON-UNIFY", null, null, null, null, null, null]
    },
    governance: {
      sla: {
        category:[],
        provider:[],
        customer:[],
        requirement:[]
      },
      requirements: {
        header:[],
        minimum:[],
        maximum:[],
        exclusiveMinimum:[],
        exclusiveMaximum:[],
        options:[],
        options_default_selected:[]
      }
    },
    lineage: {
      command:[],
      params:[],
      date:[]
    }
  };

```
