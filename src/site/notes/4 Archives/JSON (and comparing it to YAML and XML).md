---
{"dg-publish":true,"permalink":"/4-archives/json-and-comparing-it-to-yaml-and-xml/","tags":["data"],"created":"2025-11-03T22:40:45.485+07:00","updated":"2025-11-03T22:46:46.743+07:00"}
---

JSON (JavaScript Object Notation) is a lightweight text format for structuring data. It’s easy for humans to read/write and easy for machines to parse/generate. It’s language‑independent but based on a subset of JavaScript syntax.

Core ideas:
- Data types: string, number, boolean, null, object, array
- Objects: unordered key–value pairs in { } with string keys
- Arrays: ordered lists in [ ]
- Strings: double-quoted; use \ for escapes
- Commonly used for APIs, config files, and data storage

Example:
- Object with nested data: 
  `{"name":"Ada","age":36,"skills":["math","programming"],"active":true,"meta":null}`

Rules/pitfalls:
- Keys must be in double quotes
- No trailing commas
- Comments are not allowed (pure JSON)
- Dates aren’t a native type—usually strings (e.g., "2025-11-03T10:20:00Z")

Comparison:
- vs XML: more concise and easier to parse
- vs YAML: YAML is more human-friendly but more complex/ambiguous; JSON is stricter and widely supported

Typical uses:
- Web APIs exchange data in JSON
- Config files like package.json
- Storing structured logs and settings

---

**Example of XML and YAML**
![Pasted image 20251103224627.png|650](/img/user/3%20Resources/Attachment/Pasted%20image%2020251103224627.png) [ref](https://cdn.prod.website-files.com/5ff66329429d880392f6cba2/6659a312128e060ffb3da078_8%20-%2031.05-min.jpg)
![JSON comparison with XML YAML.png|650](/img/user/3%20Resources/Attachment/JSON%20comparison%20with%20XML%20YAML.png)  [ref](https://developer.ibm.com/developer/default/tutorials/yaml-basics-and-usage-in-kubernetes/images/table1.png)
XML
- Uses tags with attributes/elements
- More verbose, strictly structured
```XML
<user id="42">  
<name>Ada</name>  
<age>36</age>  
<active>true</active>  
<skills>  
<skill>math</skill>  
<skill>programming</skill>  
</skills>  
<meta/>  
</user>
```
YAML
- Uses indentation and key: value pairs
- More human-friendly; careful with spacing
```YAML
user id: 42  
name: Ada  
age: 36  
active: true  
skills:  
- math  
- programming  
meta: null
```
