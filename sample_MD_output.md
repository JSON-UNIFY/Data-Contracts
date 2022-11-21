
Runtime disconnected
PyUnify - classes.ipynb
PyUnify - classes.ipynb_
Step 1: We have a data set
[299]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
data = [
    ['ID', 'First name', 'Last name', 'Birth year', 'Height', 'Birthplace', 'Identity is secret', 'Can fly', 'Alignment', 'Wears cape'],
    ["7435", "Bruce", "Wayne", "1969*", "6'2\"", "Gotham", "Y", "3", "anti-villain", "black"],
    ["0958", "Ororo", 'Munroe', "--1979--", "5'11\"", "Manhattan", "", "9", "good", "long"],
    ["9471", "Diana", "Trevor", "1618", "5'8\"", "Paradise Island", "Y", "Jet", "truth", "rarely"],
    ["9483", "Janet", "Van Dyne", "19.42", "5'4\"", "Cresskill", "", "tiny", "Good", "Not really"],
    ["0696", "Peter", "Parker", "11111983", "5'10\"", "Queens", "Y", "Fall", "right", "never"],
    ["5531", "Harleen", "Quinzell", "1981", "6'0\"", "Gotham", "Y", "", "evil", "no"],
    ["4734", "Erik", "Lehnsherr", "1-9-8-3", "5'7\"", "Hamburg", "", "Lev.", "mutants", "Absolutely"],
    ["7757", "Natasha", "Romanova", "1983", "5'6\"", "St. Petersburg", "", "jet", "depends", "No way"],
    ["0323", "Jean", "Grey", "\"1977\"", "6'4\"", "Annandale", "", "No", "good", "Mostly not"],
    ["3980", "Clark", "Kent", "\"1954\"", "6'2\"", "Krypton", "Y", "12", "Truth", "always"],
    ["3057", "Victor", "Von Doom", "\"1943\"", "6'2\"", "Latveria", "", "1", "Bad", "yes"],
    ["0573", "Stephen", "Strange", "1968", "6'2\"", "Philidelphia", "", "not", "light", "T"],
    ["7452", "Thor", "Odinson", "2287 BC", "6'6\"", "Norway", "", "10", "Good", "Of course"],
    ["1437", "Selina", "Kyle", "1998", "5'7\"", "Gotham", "Y", "NA", "Neutral", "It clashes"],
    ["1883", "Raven", "Darkholme", "..1911..", "5'10\"", "unknown", "Y", "no", "mostly bad", "Not really"],
    ["5830", "Kara", "Zor-el", "1961", "5'7\"", "Krypton", "Y", "fast", "G", "yes"]
]
Step 2: We import it into the PyUnify wrapper

[300]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
class pyunify_governance:
  def __init__(self):
    self._init_blank_governance = {
        "compliance": [
            ["NAME", "TYPE", "DESCRIPTION", "REQUIREMENTS"],            
            
        ],
        "sla": [
            ["NAME", "TYPE", "DESCRIPTION", "REQUIREMENTS"],            
        ],
        "roles": [
            ["ROLE", "RESPONSIBILITIES"],            
        ]
    }
  
  def get(self):
    return self._init_blank_governance
  
  
[301]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
# manages internal 
class pyunify_json_unify:
  def __init__(self, _json_unify=None):
    self.json_unify = {}
    
    # is it a string?
    if type(_json_unify) == type('string'):      
      _is_json = self.is_json(_json_unify)

      #if it is not valid JSON      
      if _is_json == False:
        print("Not a valid JSON format, empty object initialized")      
        self.json_unify = self._init_json_unify()

      #if it is valid JSON
      else:        
        self.json_unify = self.json.loads(_json_unify)      
    
    #if it is a dict make sure all spec objects are there ignore all else
    elif type(_json_unify) == type({"type":"dict"}):            
      self.json_unify = self._init_json_unify()      
      keys = _json_unify.keys()
      for key in keys:
        if key not in self.json_unify:
          print('an error has occurred, there is no matching key to the specification')
        else:
          self.json_unify[key] = _json_unify[key]


    #if it is blank, create an empty JSON-Unify spec object
    elif _json_unify == None:                      
      self.json_unify = self._init_json_unify()
    
    #is it of type PyUnify?
    pass

    
  def get(self):
    return self.json_unify

  # checks if arg is valid json and returns boolean 
  def is_json(self, json_string):
    try:
      self.json.loads(json_string)
    except ValueError as e:
      return False
    return True

  def _init_governance(self):
    gov =  pyunify_governance()
    return gov.get()
    

  # returns an empty dict using the JSON-Unify specification
  def _init_json_unify(self):
    json_unify = {}
    if 'concepts' not in self.json_unify:
      json_unify['concepts'] = {
        'headers':{
          'name': [],
          'type': [],
          'description':[],
          'wikidata':[]
        }, 
        'values':{
            
        }
    }
    if 'compute' not in self.json_unify:
      json_unify['compute'] = []
    if 'custom' not in self.json_unify:
      json_unify['custom'] = {}
    if 'data' not in self.json_unify:
      json_unify['data'] = []
    if 'governance' not in self.json_unify:
      json_unify['governance'] = self._init_governance()
    if 'lineage' not in self.json_unify:
      json_unify['lineage'] = []
    if 'meta' not in self.json_unify:
      json_unify['meta'] = {}
    if 'project' not in self.json_unify:
      json_unify['project'] = {}
    return json_unify                

[334]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
# manages the 'concepts' object
class pyunify_concepts:
  def __init__(self, concepts, pd, table_render, data):    
    #init
    self.concepts = {
        'headers':{
          'name': [],
          'type': [],
          'description':[],
          'wikidata':[]
        }, 
        'values':{
            
        }
    }
    self.data = data
    
    # concepts already exists, assign    
    if concepts != {}:            
      self.concepts = concepts

    # check if concepts is empty
    if self.concepts['headers']['name'] == [] and data != None:      
      self._init_concepts_from_data(data)    

    # concepts doesn't exist, create from data if exists
    elif concepts == {} and data != None:      
      self._init_concepts_from_data(data)

    self.pd = pd
    self.table_render = table_render

  def headers(self):
    return self.concepts['headers']
  
  def values(self):
    return self.concepts['values']
        
  
  def _init_concepts_from_data(self, data):
    columns = self.data.list()[0]
    for col in columns:      
      self.headers()['name'].append(col)
      self.headers()['type'].append(None)
      self.headers()['description'].append(None)
      self.headers()['wikidata'].append(None)

  def dict(self):
    return self.concepts
  
  def table(self, render=True):         
    h_frame = self.pd.DataFrame(self.concepts['headers'])
    v_frame = self.pd.DataFrame(self.concepts['values'])    
    if render:  
      self.table_render.get("HEADERS", h_frame)   
      self.table_render.get("VALUES", v_frame)   
    return { "headers": h_frame, "values": v_frame }
  

[335]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
# manages the 'meta' object
class pyunify_meta:
  def __init__(self, meta, pd, table_render):
    if meta != {}:
      self.meta = meta
    else:
      self.meta = self._init_meta()
    self.pd = pd
    self.table_render = table_render
  
  def table(self, render=True): 
    df = self.pd.DataFrame()                   
    if self.meta != []:                
      data = []
      keys = self.meta.keys()
      for key in keys:
        val = self.meta[key]
        row = [key, val]
        data.append(row)
      df = self.pd.DataFrame(data, columns=["Key", "Value"])                    
    if render:  
      self.table_render.get("META", df)   
    return df
  
  def _init_meta(self):
    return {
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

  
[336]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
class pyunify_format:
  def __init__(self, styles=[]):
    pass
  
  # self.format(['italic', 'red']) and outputs the string
  def format(self, styles=[]):
    retVal = ""
    for style in styles:
      if style == 'italic':
        retVal += '\033[3m'
      elif style == 'default':
        retVal += '\033[0m'
      elif style == 'bold':
        retVal += '\033[1m'
      elif style == 'red':
        retVal += '\033[91m'
      elif style == 'orange':
        retVal += '\033[38;5;208m'
      elif style == 'blue':
        retVal += '\033[38;5;40m'
      elif style == 'green':
        retVal += '\033[38;5;20m'
    return retVal
[337]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
class pyunify_table_render:

  def __init__(self):
    pass
  
  def get(self, header, df=None):    
    from IPython.display import display, HTML
    h3 = "<h3 style='margin-bottom:20px; padding-bottom:0px'>{0}</h3>".format(header)        
    empty = '<i style="margin-bottom:0px;">No {0} to display.</i>'.format(header.lower())
    if not df.empty:      
      spacer = '<div style="margin-bottom:0px">&nbsp;</div>'
      display(HTML(h3), df, HTML(spacer))  
    else:      
      spacer = '<div style="margin-bottom:0px">&nbsp;</div>'
      display(HTML(h3), HTML(empty), HTML(spacer))
[338]
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
# manages the 'data' object of the PyUnify object
class pyunify_data:
  def __init__(self, data, pd, table_render):
    self.pd = pd    
    self.data = data
    self.table_render = table_render

  #instructions how to render this object as a table
  def table(self, render=True):            
    df = self.pd.DataFrame()    
    if self.data != []:                
      df = self.pd.DataFrame(data)    
      df.columns = df.iloc[0] 
      df = df[1:]           
      :
    if render:  
      self.table_render.get("DATA", df)   
    return df

  def list(self):
    return self.data

  def __str__(self):
    return str(self.data)
[402]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
class pyunify_md:
  def __init__(self, json, pd):        
    self.json = json
    self.pd = pd    
  
  def pretty(self):    
    return self.json.dumps(self._json_unify, indent=4)
  
  def benefits(self):
    title = "\n### BENEFITS\n"
    benefits = "\nNo license needed, no technology to budget, buy, or implement. Anyone can use it, an obvious and simple user experience that will help entire teams."
    goal = "\nThe purpose and benefit of using JSON-Unify is to improve the user experience of those who create, consume, and share data by reducing ambiguitiy and saving time.\n\n"
    return title+benefits+goal

  def wrapper(self):
    title = "\n### PyUnify IS A WRAPPER TO MAKE WORKING WITH JSON-UNIFY EASY\n"
    rec1 = "\n- PyUnify is a Python library that auto-generates and adds recommended JSON-Unify properties, as well as helper functions like exporting .MD files."
    rec2 = "\n- View the **specification** and **recommendations** to further enrich your data in the specification at: https://github.com/JSON-UNIFY."  
    rec3 = "\n- For example, a few 'meta' recommended fields are: a description of the data, the source of the data, the author of the data, the data contract URL."    
    return title+rec1+rec2+rec3
    

  def specification(self):
    specification = "\n### THE SPECIFICATION\n"
    requirements = "\n\nJSON-Unify is a <em>minimal & simple specification</em> requiring **metadata**, **concepts**, and **data** are in one self-contained JSON object."
    example = "\n```\nJSON-Unify = {\n\tconcepts: {},\n\tdata: {},\n\tmeta: {}\n}\n```\n"  
    compatibility = "\nYou can have a pointer (URL reference) to the data if the data is large or if the data is not in JSON format. This still provides a single object in JSON format that can be used to communicate data"
    return specification + requirements + example + compatibility

  def instantiate(self):    
    specification = "\n### USING PyUnify\n"
    step1 = "\nTo instantiate this JSON-Unify data contract with PyUnify:\n"
    step2 = "\n- Copy the JSON code in this MD file below.\n- In your **Python Notebook**:\n```\n\n!pip install PyUnify\nimport PyUnify\nunify = PyUnify(paste_json_from_this_MD_file)\n```\n"    
    return step1+step2

  def generate(self):
    line1 = "\nThis markdown file was automatically generated with \n```\nunify.md()\n```\n"
    line2 = "\nTo edit the title of the documentation use: \n```\nunify.md({'title':'My title here'})\n```\n"
    line3 = "\nOtherwise, the title will be auto-generated from the meta name property"
    return line1+line2+line3
    

  def instructions(self):
    instructions = ""
    instructions += self.specification()
    instructions += self.benefits()
    instructions += self.wrapper()
    instructions += self.instantiate()
    instructions += self.generate()    
    return instructions

  def title(self, title=None):
    if title == None:
      return "# Auto-generate JSON-Unify documentation with PyUnify\n\n"
    else:
      return "# {0}".format(title)

  def get(self, data_frames):    
    markdown = ""    
    markdown += self.title()
    markdown += self.instructions()
    for df in data_frames:      
      header=df['header']
      table = df['table'].to_markdown()
      markdown += "## {0}\n\n```\n{1}\n```\n".format(header, table)
    print(markdown)

      

    
    
    
    

[403]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
# the PyUnify object
class PyUnify:
  def __init__(self, json_unify=None):   
    self._init_dependencies()
    table_render = pyunify_table_render()

    #creates an initialized json_unify wrapper object
    self._json_unify = pyunify_json_unify(json_unify).get()  

    self._md = pyunify_md(self.json, self.pd)  
    self._meta = pyunify_meta(self._json_unify['meta'], self.pd, table_render)    
    self._data = pyunify_data(self._json_unify['data'], self.pd, table_render)
    
    self._concepts = pyunify_concepts(self._json_unify['concepts'], self.pd, table_render, data = self._data)
    
    
  def _init_dependencies(self):
    import pandas as pd
    self.pd = pd
    self.pd.set_option('max_colwidth', 1024)    

    import json as json
    self.json = json

  def table(self, keys=[], render=True):
    if keys == []:
      keys = ['concepts', 'data', 'meta', 'governance', 'compute', 'custom', 'lineage', 'project']
    for key in keys:
      if key == 'data':        
        self._data.table(render)
      if key == 'meta':
        self._meta.table(render)
      if key == 'concepts':
        self._concepts.table(render)
      if key == 'governance':
        self._governance.table(render)

  def data(self):
    return self._data.list()

  def concepts(self):
    return self._concepts.dict()
    
  def md(self, keys=[]):    
    data_frames = [
        {
            'header': 'Concepts - Headers',
            'table':self._concepts.table(False)['headers']
        },
        {
            'header': 'Concepts - Values',
            'table':self._concepts.table(False)['values']
        },
        {
            'header': 'Data',
            'table':self._data.table(False)
        },
        {
            'header': 'Meta',
            'table':self._meta.table(False)
        },
        {
            'header': 'Governance - SLA',
            'table':self._meta.table(False)
        }
        
    ]
    return self._md.get(data_frames)

  def __str__(self):    
    return str(self._json_unify)

  def __repr__(self):    
    return str(self._json_unify)  
[404]
0s
  1
  2
  3
  4
  5
  6
  7
  8
#import PyUnify

unify = PyUnify({'data':data})
#unify = PyUnify()
unify.md()
#unify.table(['concepts', 'meta', 'data'])
#unify.table()

# Auto-generate JSON-Unify documentation with PyUnify


### THE SPECIFICATION


JSON-Unify is a <em>minimal & simple specification</em> requiring **metadata**, **concepts**, and **data** are in one self-contained JSON object.
```
JSON-Unify = {
	concepts: {},
	data: {},
	meta: {}
}
```

You can have a pointer (URL reference) to the data if the data is large or if the data is not in JSON format. This still provides a single object in JSON format that can be used to communicate data
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

PREVIOUS CODE
[362]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603
604
605
606
607
608
609
610
611
612
613
614
615
616
617
618
619
620
621
622
623
624
625
626
627
628
629
630
631
632
633
634
635
636
637
638
639
640
641
642
643
644
645
646
647
648
649
650
651
652
653
654
655
656
657
658
659
660
661
662
663
664
665
666
667
668
669
670
671
672
673
674
675
676
677
678
679
680
681
682
683
684
685
686
687
688
689
690
691
692
693
694
695
696
697
698
699
700
701
702
703
704
705
706
707
708
709
710
711
712
713
714
715
716
717
718
719
720
721
722
723
724
725
726
727
728
729
730
731
732
733
734
735
736
737
738
739
740
741
742
743
744
745
746
747
748
749
750
751
752
753
754
755
756
757
758
759
760
761
762
763
764
765
766
767
768
769
770
771
772
773
774
775
776
777
778
779
780
781
782
783
784
785
786


class PyUnify:

  #__slots__['json_unify'] ?

  # intialized the JSON-Unify object
  # takes in no arguments and it will create a new self.json_unify object
  # or, takes in an object named json which has 8 categories
  def __init__(self, _json_unify=None):
    
    self.json_unify = {}    
    self._init_dependencies()    



    

    
    

    

    
  
    req_keys = list(self.json_unify)    
    for key in req_keys:      
      if key != "meta" and key != 'concepts' and key != 'data' and key != 'custom' and key != 'compute' and key != 'project' and key != 'governance' and key != 'lineage':
        print("Init object \033[91mDOES NOT\033[0m meet requirements. Only 'meta', 'concepts', 'data', 'custom', and 'compute allowed.\n")
        print('key:', key,'\nvalue: ',self.json[key], '\n')
    
    self._init_dict()
    
    #self.compute_setNumRows()
  
  #def compute_setNumRows(self):
    #num_rows = self.json['data'].len() - 1
    #print(num_rows)

  

  
  def _init_dict(self):
    if "meta" not in self.json_unify:
      self.json_unify["meta"] = self._init_blank_meta
    else:
      self.meta_setInitValues()
    
    if "compute" not in self.json_unify or self.json_unify['compute'] == []:      
      #self.json_unify["compute"] = [
          #['STATE', 'VALUE', 'LISTENER', 'EVENT', 'DESCRIPTION'],
          ##['NUM_ROWS', None, None, None, 'The number of rows in the dataset'],
          #['NUM_COLUMNS', None, None, None, 'The number of columns in the dataset'],
          #['DATE_CREATED', None, None, None, 'The date this object was created'],
          #['DATE_MODIFIED', None, None, None, 'The date his object was last modified'],          
      #]
      self.json_unify["compute"] = []    

    if "governance" not in self.json_unify:
      self.json_unify['governance'] = self._init_blank_governance
      #self.json_unify["governance"] = []
      #self.governance_init()
    elif self.json_unify['governance'] == {}:
      self.json_unify['governance'] = self._init_blank_governance

    if "lineage" not in self.json_unify or self.json_unify["lineage"] == []:
      self.json_unify["lineage"] = []    
      self.lineage_init()    

    if "data" not in self.json_unify:
      self.json_unify["data"] = []
      self.data_initFromConcepts()

    if "concepts" not in self.json_unify:
      self.json_unify["concepts"] = {"headers":{}, "values":{}}
      self.concepts_initFromData()
    elif self.json_unify['concepts'] == {} and self.json_unify['data'] != []:      
      self.concepts_initFromData()
    elif self.json_unify['concepts'] == {}:
      self.json_unify["concepts"] = {"headers":{}, "values":{}}
    
    if 'custom' not in self.json_unify:
      self.json_unify['custom'] = {}

  

  def governance_init(self):
    self.json_unify['governance'] = self._init_blank_governance

  def lineage_init(self):
    
    import datetime;
    ct = datetime.datetime.now()
    ct = ct.strftime("%m/%d/%Y, %H:%M:%S")      
    _init_blank_lineage = [
      ["LISTENER", "EVENT", "DESCRIPTION", "TIMESTAMP"],
      ["data", "init", "data initialized", ct],
      ["concepts", "init", "concepts initialized", ct],
      ["meta", "init", "meta initialized", ct],
      ["governance", "init", "governance initialized", ct]      
    ]
    self.json_unify['lineage'] = _init_blank_lineage    

  def _init_dependencies(self):
    import pandas as pd
    self.pd = pd
    self.pd.set_option('max_colwidth', 1024)    

    import json as json
    self.json = json

  def meta_setInitValues(self):
    meta = self.json_unify['meta']
    for key in self._init_blank_meta:
      if key not in meta:
        meta[key] = self._init_blank_meta[key]

  def data_initFromConcepts(self):
    row = []
    for concept in self.json_unify['concepts']['headers']:
      row.append(concept)
    self.json_unify['data'].append(row)

  def concepts_initFromData(self):
    #for each column in data, add a key, type, and description in concepts
    headers = self.json_unify['concepts']['headers']
    for column_name in self.json_unify['data'][0]:
      headers.append({
          "name":column_name,
          "type": None,
          "description": None
      })
      #self.json_unify['concepts']['headers']['name'] = column_name
      #self.json_unify['concepts']['headers']['type'] = None
      #self.json_unify['concepts']['headers']['description'] = None



#CONCEPTS METHODS


  def concept(self, name, params):        
    #key = list(params.keys())[0]
    #find row number of concept name
    #find key 
    # UPDATE param from concepts where 'name' = name
    #self.json_unify['concepts']['headers'][name] = params[key]
    return 'NEEDS TO BE FIXED'
  
  def concept_highlight(self, key):
    return self.concepts_toTable(key, {'color':'blue', 'font-weight':'bold'})
  
  def concepts(self, params=None):        
    if params == None:      
      return self.json_unify['concepts']      
    elif 'format' in params:
      if params['format'].lower() == 'markdown':                        
        headers = self.concepts_headers_getDataFrame()
        values = self.concepts_values_getDataFrame()
        return {'headers':headers.to_markdown(), 'values':values.to_markdown()}
    #elif 'set' in params:
      ##kv_pairs = params['set']
      #for key in kv_pairs:
        #val = kv_pairs[key]
        #self.json_unify['concepts'][key] = val      
    else:
      print('Unknown params: ', params)

  # returns a list of dict objects for each concept header row
  def concepts_getHeaders(self):
    headers = self.json_unify['concepts']['headers']
    return headers

# DATA METHODS
  

  def data_getColumnNumber_byColumnName(self, columnName):
    data = self.json_unify['data']
    columns = data[0]
    
    col_num = columns.index(columnName)
    return col_num

  def data_getRows_byColumnNumber(self, col_num):
    data = self.json_unify['data']
    column = []
    for row in data:
      cell = row[col_num]
      column.append(cell)
    column.pop(0)
    return column

  
  
  def compute(self, compute=None):    
    if compute != None:      
      self.json_unify['compute'] = compute
    else:
      return self.json_unify['compute']
  
  
  
  

  def pandas_format_cell_style_by_string_match(self, val, str_to_match, params):        
    retVal = ''
    if val == str_to_match:
      props = list(params.keys())
      for prop in props:
        retVal += "{0}:{1}; ".format(prop, params[prop])    
    return retVal
    

  
  def columnNames(self):
    if 'columns' in self.json_unify['concepts']:
      col_names = list(self.json_unify['concepts']['headers'].keys())
      return col_names
    else:
      #print('No columns defined in "concepts" key')
      return []

  def describeColumn(self, name):
    col_desc = None    
    col_desc = self.json_unify['concepts']['headers'][name]['description']
    return col_desc

  def getColumnDesriptionRow(self, col):
    row = []
    col_name = col
    col_type = None
    col_desc = None
    columns = self.json_unify['concepts']['headers']
    if col in columns:
      if 'type' in columns[col]:
        col_type = columns[col]['type']        
      if 'description' in columns[col]:
        col_desc = columns[col]['description']          
    row.append(col_name)
    row.append(col_type)
    row.append(col_desc)
    return row

  

  
    

  def getMetadataData(self):
    keys = list(self.json_unify['meta'].keys())
    rows = []
    for key in keys:            
      row = [key, self.json_unify['meta'][key]]
      rows.append(row)          
    return rows

# QUALITY METHODS
  
  # will recommend changes to concepts and data values to use higher quality data best practices
  def quality(self):
    headers = self.concepts_getHeaders()    
    warnings = 0
    for header in headers:
      if 'name' in header:
        name = header['name']
        #if (name.lower() == 'id' or name.lower() == 'uid'):
        #if column[1] != 'int':
          #warnings += 1
          #print("{0}WARNING[{3}]{1}: It is recommended that for concepts in the {2} column you use the 'int' type".format(self.format(['orange', 'bold']), self.format(['default']), column_name, warnings))
          #print("\n{0}To make this change, you can run:{1}".format(self.format(['italic']), self.format(['bold'])))
          #print("\tunify_obj_name.clean({'concept': {'ID': {'type':'int'}})")
          #print("{0}\n".format(self.format(['default'])))
        if (name.lower() == 'height' or name.lower() == 'width'):        
          warnings += 1
          print("{0}WARNING[{3}]{1}: It is recommended that for dimensional concepts in the {2} column you describe the measure, such as inches, cm, meters, etc.".format(self.format(['orange', 'bold']), self.format(['default']), name, warnings))
          print("\n{0}To make this change, you can run:{1}".format(self.format(['italic']), self.format(['bold'])))
          print("\tunify_obj_name.clean({'concept': {'width': {'name':'Width_In_Inches'}})")
          print("{0}".format(self.format(['default'])))

        if ("year" in name.lower() or name.lower() == 'date'):        
          warnings += 1
          print("{0}WARNING[{3}]{1}: It is recommended that for data & time concepts in the {2} column you use the standard DDMMYYYY".format(self.format(['orange', 'bold']), self.format(['default']), name, warnings))
          print("\n{0}To make this change, you can run:{1}".format(self.format(['italic']), self.format(['bold'])))
          print("\tunify_obj_name.clean({'concept': {'date_column': {'type':'date'}})")
          print("{0}".format(self.format(['default'])))
          




  def lineage(self, params=None):        
    if params == None:      
      return self.json_unify['lineage']
    elif 'format' in params:
      if params['format'].lower() == 'markdown':                
        return self.table_lineage(False).to_markdown()
    elif 'set' in params:
      print("set functionality not implemented currently")
    else:
      print('Unknown params: ', params)

  def governance(self, params=None):        
    if params == None:      
      return self.json_unify['governance']
    elif 'format' in params:
      if params['format'].lower() == 'markdown':                        
        gov = self.table_governance(False)        
        for key in gov:
          gov[key] = gov[key].to_markdown()          
        return gov
    elif 'set' in params:
      print("set functionality not implemented currently")
    else:
      print('Unknown params: ', params)

  def concepts_toTable(self, string_to_match=None, new_params=None):
    data = self.getDataConcepts()        
    df = pd.DataFrame(data, columns=['Column Name', 'Type', 'Description'])    
    if new_params != None:                  
      df = df.style.applymap(self.pandas_format_cell_style_by_string_match, str_to_match = string_to_match, params = new_params)    
    return df

  

  #will analyze concepts for 'description' and report missing keys
  def concepts_validate_descriptions(self):
    true_count = 0
    false_count = 0
    print("\n\033[0m\033[1mCHECKING 'Description' PROPERTY IN CONCEPTS...\n")
    concepts = self.json_unify['concepts']['headers']
    for concept in concepts:      
      if 'description' in concept and 'name' in concept:
        description = concept['description']
        msg = "\033[0m{0}: \033[92m\033[1mTrue".format(description)                
        print(msg)
        true_count = true_count+1
      else:
        msg = "\033[0m{0}: \033[91m\033[1mFalse".format(description)        
        print(msg)
        false_count = false_count+1
    print("\n\033[0m\033[3m'Description' property DOES exist in {0} columns, 'Description' property DOES NOT exist in {1} columns\n".format(true_count, false_count))

  #will analyze concepts for 'types' and report missing keys
  def concepts_validate_types(self):
    true_count = 0
    false_count = 0
    print("\n\033[0m\033[1mCHECKING 'Type' PROPERTY IN CONCEPTS...\n")
    concepts = self.json_unify['concepts']['headers']
    for concept in concepts:      
      if 'type' in concept and 'name' in concept:
        name = concept['name']
        msg = "\033[0m{0}: \033[92m\033[1mTrue".format(name)                
        print(msg)
        true_count = true_count+1
      else:
        msg = "\033[0m{0}: \033[91m\033[1mFalse".format(name)        
        print(msg)
        false_count = false_count+1
    print("\n\033[0m\033[3m'Type' property DOES exist in {0} columns, 'Type' property DOES NOT exist in {1} columns\n".format(true_count, false_count))

  #will analyze concepts for 'types' and 'description' and report missing keys
  def concepts_validate(self):
    self.concepts_validate_types()
    self.concepts_validate_descriptions()

# DATA METHODS
  def data(self, params=None):        
    if params == None:      
      return self.json_unify['data']      
    elif 'format' in params:
      if params['format'].lower() == 'markdown':                
        return self.table_data(False).to_markdown()
    elif 'set' in params:
      kv_pairs = params['set']
      for key in kv_pairs:
        val = kv_pairs[key]
        self.json_unify['data'][key] = val      
    else:
      print('Unknown params: ', params)

# HELP METHODS

  def help(self, type_of = None):
    if type_of == None:
      print("""        
        - \033[1mThe JSON-UNIFY Object Specification\033[0m
          - The JSON object MUST contain a 'meta', 'concepts', and 'data' key                        
        
          - \033[1mCONCEPTS\033[0m
            - \033[1mThe obj['concepts'] key MUST contain:\033[0m
              - 'columns': concept definitions for column headers
                - EACH column MUST have the following items:
                  - 'type': the type (int, string, etc.)
                  - 'description': a description of the concept
                              
            - \033[1mThe obj['concepts']['headers'] key is RECOMMENDED to contain:\033[0m
              - 'values': concept definitions for values inside a columns
              - 'uri': any knowledge base information, such as from wikidata
              - 'examples': a collection of examples
              - 'relations': a collection of relations such as
                - 'is a'
                - 'part of'
                - 'has kind'
                - 'has instance'
                - 'category domain'
                - 'has quality'
                - 'studied by'
            
            - \033[1mThe obj['concepts'] key CAN contain:\033[0m
              - 'groups': a dictionary of a group with the column names of the group
                - example: 'height', and 'width' columns can be in a group called 'physical dimensions'
                  - 'group': {
                    "dimensions": [
                      "height",
                      "width
                    ]                                          
                  }

              
          - \033[1mDATA\033[0m
            - \033[1mThe 'data' key MUST contain:\033[0m
              - data in the form of rows (an array of arrays, where the inner array represents one row)
                example - 'data': [['col1', 'col2'], [1, 3], [2, 4]] 

              - FUTURE FEATURE: data in the form of columns (an object where each key represents the column header, and each row is in an array)
                example - 'data': {'col1': [1, 2], 'col2': [3, 4]}            

          - \033[1mMETA\033[0m
            - \033[1mThe 'meta' key MUST contain:\033[0m
              - 'source': where the data came from
              - 'contract': which JSON-Unify contract is being used (see GitHub page or json-unify.org)
                - default:
                   - https://github.com/JSON-UNIFY                      
              - 'description': a description about the data set
          
            - \033[1mThe 'meta' key CAN contain:\033[0m              
              - 'authors': any author names / owner names
              - 'tags': any comma-separated tags for search
              - 'contact': any contact information (team name, person email address, etc.)
              - 'custom': anything custom 
              - 'id': a unique ID for the JSON-Unify objects 
              - 'license': any license information

          - \033[1mCOMPUTE\033[0m
            - \033[1mThe 'compute' key MUST contain:\033[0m
              - 'state': any associated state of the object's internal variables managed by the object
              - 'value': any associated value of a state of the object's internal variables managed by the object
              - 'listener': the function listening for an event
              - 'event': a boolean conditional for the event that triggers the listener's function to execute
              - 'description': what the function does
              
                

          
        - \033[1mAbout the JSON-Unify Specification\033[0m
          - GitHub: \033[94mhttps://github.com/JSON-UNIFY\033[0m
          - Website: 033[94mhttps://json-unify.org\033[0m
          - License: \033[94mhttps://www.gnu.org/licenses/gpl-3.0.en.html\033[0m
          - Contributors: Ron Itelman, Cameron Prybol, Stephanie Bankes
        
        - \033[1mAbout the JSON-Unify Implementation\033[0m
          - GitHub: \033[94mhttps://github.com/JSON-UNIFY\033[0m
          - Website: \033[94mhttps://json-unify.org\033[0m
          - License: \033[94mhttps://www.gnu.org/licenses/gpl-3.0.en.html\033[0m
          - Contributors: Ron Itelman, Cameron Prybol, Stephanie Bankes

        - \033[1mJSON-Unify Implementation API\033[0m
          - meta_validate() 
            - Description: Will analyze 'meta' top-level key and look for missing requirements
            - Parameters: None
            - Outputs: Prints text
            - Returns: None

          - concepts_validate()
            - Description: Will analyze 'concepts' top-level key and look for missing requirements
            - Parameters: None
            - Outputs: Prints text
            - Returns: None
        
        
      """)


#MARKDOWN METHODS
  def md(self):    
    

#META METHODS
  
  def meta(self, params=None):        
    if params == None:      
      return self.json_unify['meta']      
    elif 'format' in params:
      if params['format'].lower() == 'markdown':                
        return self.table_meta(False).to_markdown()
    elif 'set' in params:
      kv_pairs = params['set']
      for key in kv_pairs:
        val = kv_pairs[key]
        self.json_unify['meta'][key] = val      
    else:
      print('Unknown params: ', params)

  #will analyze 'meta' top-level key and look for missing requirements
  def meta_validate(self):
    total_req_props = 3
    has_req_props = 0
    total_rec_props = 4
    has_rec_props = 0
    has_contract = False
    has_source = False
    has_description = False
    has_authors = False
    has_license = False
    has_contact = False
    has_id = False
    print("\n\033[0m\033[1mCHECKING META...\n")
    if 'contract' in self.json_unify['meta']:
      has_contract = True      
      has_req_props = has_req_props + 1
      msg = "\033[0mCONTRACT (required): \033[92m\033[1m{0}".format(has_contract)
    else:
      msg = "\033[0mCONTRACT (required): \033[93m\033[1m{0}".format(has_contract)
    print(msg)
    if 'source' in self.json_unify['meta']:
      has_source = True
      has_req_props = has_req_props + 1
      msg = "\033[0mSOURCE (required): \033[92m\033[1m{0}".format(has_source)
    else:
      msg = "\033[0mSOURCE (required): \033[93m\033[1m{0}".format(has_source)
    print(msg)
    if 'description' in self.json_unify['meta']:
      has_description = True
      has_req_props = has_req_props + 1
      msg = "\033[0mDESCRIPTION (required): \033[92m\033[1m{0}\n".format(has_description)
    else:
      msg = "\033[0mDESCRIPTION (required): \033[93m\033[1m{0}".format(has_description)
    print(msg)
    if 'authors' in self.json_unify['meta']:
      has_authors = True 
      has_rec_props += 1     
      msg = "\033[0mAUTHOR (recommended): \033[92m\033[1m{0}".format(has_authors)
    else:
      msg = "\033[0mAUTHOR (recommended): \033[94m\033[1m{0}".format(has_authors)
    print(msg)
    if 'license' in self.json_unify['meta']:
      has_license = True 
      has_rec_props += 1     
      msg = "\033[0mLICENSE (recommended): \033[92m\033[1m{0}".format(has_license)
    else:
      msg = "\033[0mLICENSE (recommended): \033[94m\033[1m{0}".format(has_license)
    print(msg)
    if 'id' in self.json_unify['meta']:
      has_id = True 
      has_rec_props += 1     
      msg = "\033[0mID (recommended): \033[92m\033[1m{0}".format(has_id)
    else:
      msg = "\033[0mID (recommended): \033[94m\033[1m{0}".format(has_id)
    print(msg)
    if 'contact' in self.json_unify['meta']:
      has_contact = True 
      has_rec_props += 1     
      msg = "\033[0mCONTACT (recommended): \033[92m\033[1m{0}".format(has_contact)
    else:
      msg = "\033[0mCONTACT (recommended): \033[94m\033[1m{0}".format(has_contact)
    print(msg)
    print("\n\033[0m\033[3m{0}/{0} required properties DO exist, {1} required properties ARE MISSING\n{2} recommended properties DO exist, {3} recommended properties ARE MISSING".format(has_req_props, total_req_props - has_req_props, has_rec_props, total_rec_props - has_rec_props))

# PRETTY JSON METHODS



# TABLE METHODS

  def tables(self, views=['compute', 'concepts', 'custom', 'data', 'meta', 'lineage', 'governance']):        
    for view in views:
      if view == 'meta':
        self.table_meta()
      elif view == 'data':
        self.table_data()
      elif view == 'concepts':
        self.table_concepts()
      elif view == 'headers':
        self.table_concepts_headers()
      elif view == 'values':
        self.table_concepts_values()
      elif view == 'compute':
        self.table_compute()
      elif view == 'custom':
        self.table_custom()
      elif view == "all":
        self.table_all()
      elif view == "lineage":
        self.table_lineage()
      elif view == 'governance':
        self.table_governance()
    
  
  

  def concepts_headers_getDataFrame(self):                    
    #columns = ["COLUMN NAME", "TYPE", "DESCRIPTION", "WIKIDATA URL"]
    data = self.json_unify['concepts']['headers']    
    return self.pd.DataFrame(data= data)
  
  def concepts_values_getDataFrame(self):                        
    data = self.json_unify['concepts']['values']
    return self.pd.DataFrame(data)

  def table_concepts_headers(self, render=True):    
    headers = self.concepts_headers_getDataFrame()
    if render:
      self.table_render("CONCEPTS - HEADERS", headers)

  def table_concepts_values(self, render=True):    
    values = self.concepts_values_getDataFrame()
    if render:
      self.table_render("CONCEPTS - VALUES", values)

  def table_concepts(self, render=True):        
    headers = self.table_concepts_headers(render)
    values = self.table_concepts_values(render)    
    

    

  def table_governance(self, render=True):        
    sla = self.json_unify['governance']['sla']
    roles = self.json_unify['governance']['roles']
    compliance = self.json_unify['governance']['compliance']
    if sla != []:                      
      df1 = self.pd.DataFrame(sla)          
      df1.columns = df1.iloc[0] 
      df1 = df1[1:]
    if roles != []:                      
      df2 = self.pd.DataFrame(roles)          
      df2.columns = df2.iloc[0] 
      df2 = df2[1:] 
    if compliance != []:                      
      df3 = self.pd.DataFrame(compliance)
      df3.columns = df3.iloc[0] 
      df3 = df3[1:] 
    else:
      df1 = self.pd.DataFrame()      
      df2 = self.pd.DataFrame()      
      df3 = self.pd.DataFrame()    
    if render:  
      self.table_render("GOVERNANCE - ROLES", df2)   
      self.table_render("GOVERNANCE - SLA", df1)   
      self.table_render("GOVERNANCE - COMPLIANCE", df3)   
    return {"sla":df1, "roles":df2, "compliance":df3}

  def table_lineage(self, render=True):    
    lineage = self.json_unify['lineage']
    if lineage != []:                      
      df = self.pd.DataFrame(lineage)
      df.columns = df.iloc[0] 
      df = df[1:]    
    else:
      df = self.pd.DataFrame()      
      df2 = self.pd.DataFrame()      
      df3 = self.pd.DataFrame()       
    if render:   
      self.table_render("LINEAGE", df)   
    return df


  def table_compute(self):    
    data = self.json_unify['compute']
    if data != []:                      
      df = self.pd.DataFrame(data)          
      df.columns = df.iloc[0] 
      df = df[1:] 
    else:
      df = self.pd.DataFrame()      
    self.table_render("COMPUTE", df)   
    return df

  def table_custom(self):    
    data = self.json_unify['custom']
    if data != {}:
      df = self.pd.DataFrame(data)          
    else:
      df = self.pd.DataFrame()      
    self.table_render("CUSTOM", df)                                    
    return df
  
  def table_data(self, render=True):    
    data = self.json_unify['data']    
    if data != []:                
      df = self.pd.DataFrame(data)    
      df.columns = df.iloc[0] 
      df = df[1:]       
    else:
      df = self.pd.DataFrame()    
    if render:  
      self.table_render("DATA", df)   
    return df
  
  def table_meta(self, render=True):    
    meta = self.getMetadataData()        
    if meta != []:                  
      df = self.pd.DataFrame(meta, columns=["Key", "Value"])         
    else:      
      df = self.pd.DataFrame()     
    if render:
      self.table_render("META", df) 
    return df

  def table_render(self, header, df=None):    
    from IPython.display import display, HTML
    h3 = "<h3 style='margin-bottom:20px; padding-bottom:0px'>{0}</h3>".format(header)    
    #help_func = '<b>PyUnify.help({"tables":"'+header.lower()+'"})</b>'
    empty = '<i style="margin-bottom:0px;">No {0} to display.</i>'.format(header.lower())
    if not df.empty:      
      spacer = '<div style="margin-bottom:0px">&nbsp;</div>'
      display(HTML(h3), df, HTML(spacer))  
    else:      
      spacer = '<div style="margin-bottom:0px">&nbsp;</div>'
      display(HTML(h3), HTML(empty), HTML(spacer))

  def table_spec(self):       
    self.pd.set_option('max_colwidth', 1024)        
    self.table_concepts()        
    self.table_data()    
    self.table_meta()
    
    
  
# TEST METHODS    

  # loops through each column, gets the type, and then loops through each value to validate the type
  def test(self, language="python"):
    concepts = self.json_unify['concepts']['headers']
    print("\033[0mLANGUAGE\033[0m: \033[1m{0}\033[0m\n".format(language))
    for column_name in concepts:
      #get the column number of the column_name
      col_num = self.data_getColumnNumber_byColumnName(column_name)        
      #get all values in the column by column number
      column = self.data_getRows_byColumnNumber(col_num)                            
      if 'type' in concepts[column_name]:        
        _type = concepts[column_name]['type']  
        #check each value against _type
        print("\033[1m{0}".format(column_name))
        for cell in column:
          self.test_cell(_type, cell, language)
          
      else:
          print("\033[1m{0}: \t\033[0m\033[91mNo type defined for {0}\033[0m".format(column_name))                            
      print("\n")

  def test_cell(self, _type, cell, language):
    language = language.lower()

    boolean = None
    string = None

    if (language == 'python'):
      boolean = 'bool'
      string = 'str'

    if (language == 'javascript'):
      boolean = 'boolean'
      string = 'string'

    if _type == boolean:
      if type(cell) != type(True):
        print('\t\033[0m\033[91mFAIL\033[0m: {0}, expecting {1}, found {2}'.format(cell, _type, type(cell)))              
      else:
        print('\t\033[0m\033[92mPASSED\033[0m: {0}, expecting {1}, found {2}'.format(cell, _type, type(cell)))
    if _type == string:
      if type(cell) != type("string"):
        print('\t\033[0m\033[91mFAILED\033[0m: {0}, expecting {1}, found {2}'.format(cell, _type, type(cell)))
      else:
        print('\t\033[0m\033[92mPASSED\033[0m: {0}, expecting {1}, found {2}'.format(cell, _type, type(cell)))    
        

# VALIDATE METHODS

  def validate(self):
    self.meta_validate()
    self.concepts_validate()
    
  
   


SAMPLE DATA SET: BRANDON'S SUPERHUMAN MICROSOFT PRESENTATION
Imagine we have a data source, it could be tabular data in csv format, pandas, SQL output, or JSON.

WHAT DOES "IDENTITY IS SECRET MEAN"?
The following is an example of data that was retrieved from a query, what do the headers mean? For example, does "Identity is secret" mean it is a secret from other superhumans as well? What about relationships? Does it only apply to the general public?

WHAT ESTIMATOR ALGORITHMS CAN I USE WITH THIS DATA SET?
[ ]
↳ 1 cell hidden
We don't know much about our data
there is no metadata
there is no description of the concepts in the columns or in the values
there is no description of what the describe function is giving me
Sometimes people write functions to find missing values and clean data
Sometimes people start randomly visualizing columns
Sometimes we would identify a target value
[ ]
↳ 1 cell hidden
Introducing the JSON-Unify Specification
Guarantees the metadata, the data, and the concepts of the data in a single payload
Simply adding these to a JSON payload will reduce the top productivity-destroying issues data teams have:

The "metadata" key has data about the data
The "data" key has the actual data
The "concepts" key has definitions about the data
A Day In The Life Of A Data User
You open up a data set
You have no idea what the columns mean
You have no idea what is valuable, or what is missing
You don't know which algorithms can you use effectively with your data
You waste a tremendous amount of time trying to figure this out
You pass it off to the next person who has to go through all of this again
We want to break that productivity-destroying experience.
We want to make the world a bit better of a place for our data community.
[ ]
↳ 1 cell hidden
Adding Metadata
Our first problem is that we have data and we know nothing about it. The data has no metadata along with it. Where does it come from? What tables where used, what was the query that outputted the data? Where are the schemas for the tables so types can be reviewed?

This can mean our data scientists have to spend a lot of time looking, researching, setting up meetings, etc., which takes from a lot of people's time. It also means that the data scientist has no context and could misunderstand things.

[ ]
↳ 1 cell hidden
Adding concept definitions to our data
One problem with this data set is that we don't know what the columns mean.

For example, does "Identity is secret" mean that a super hero has shared their identiy with other heroes but not regular humans?

In our concepts sections we simply need to add a description for each column, and the type

[ ]
↳ 1 cell hidden
Create an object using the JSON-Unify specification
no technology
metadata is with the data
concepts is with the data
This alone will save your team a lot of time
[ ]
↳ 1 cell hidden
PyUnify is a wrapper around a JSON-Unify object, turning it into an 'app'
- Automatically generate GitHub documentation, such as .MD files
- Automate data quality checks
- Automatically add semantic information to your data
- Use templates for best practices
[ ]
↳ 2 cells hidden
unify.tables(['concepts', 'data', 'meta'])
Specify which tables to generate
[ ]
↳ 2 cells hidden
Unify.validate() checks if your PyUnify object meets JSON-Unify specifications
META
contract
source
description
CONCEPTS
name
type
description
Non-required but recommended attributes are shown as well

[ ]
↳ 1 cell hidden
unify.help() describes PyUnify help methods
[ ]
↳ 1 cell hidden
unify.pretty() prints pretty-formatted JSON
[ ]
↳ 1 cell hidden
unify.quality()
Recommends cleaning columns names
Recommends cleaning columns values
[ ]
↳ 1 cell hidden
unify.sql(query_string)
Run SQL to transform your data
[ ]
↳ 1 cell hidden
Easily change concept properties & values
Add styling to elements
Change a concept type by name
[ ]
↳ 2 cells hidden
unify.define()
Recommends wikidata references
Recommends column definitions = Recommends value definitions
For City in concepts use: https://www.wikidata.org/wiki/Q515 For "San Francisco" in the "City" column, use: https://www.wikidata.org/wiki/Q62

unify.object()
Turns each row into an object
Uses unify.schema()
[ ]
↳ 1 cell hidden
unify.schema()
defines a schema to convert a row into an object
uses JSON-Schema
unify.ld()
Defines data in JSON-LD
[ ]
↳ 1 cell hidden
unify.project()
unify.lineage()
unify.governance()
Future Feature Ideas
Group of JSON-Unify objects can self organize
Save JSON-Unify template, so that data can be swapped out but concepts and meta stay the same
NLP to auto-generate description in meta
NLP to autogenerate type and description in concepts for columns and/or values
Test how much storage JSON-Unify object takes up compared to the data
Pretty print JSON
Adding compute functions to the JSON-Unify object to be executed
Adding ML decision tree
Visualize flow chart of data
Autogenerate json-schema
Autogenerate json-ld
Import/export SQL schema file
Use Python 3.11
Write concepts URI knowledge base to GitHub
Connect to APIs (GitHub, etc.)
[ ]
↳ 3 cells hidden
Copy and paste JSON from a GitHub .MD file to create a PyUnify object
[ ]
↳ 2 cells hidden
Colab paid products - Cancel contracts here

check
0s
completed at 9:38 AM
Made 1 formatting edit on line 44
