The INI file format was chosen for EditorConfig due to its ease of use.  Some of the thought process that resulted in the current INI-based EditorConfig format is included below.

## INI format

### Required modifications to this format

* Allow any characters to appear in section names (not just alphanumeric and certain symbols).  For example:

```ini
[*[1964].txt]
indent_style = space
indent_size = 2
```

### Possible modifications to this format

* Allow property declarations outside of section names (at top of file only).  For example:

```ini
root = true
[*.py]
indent_style = space
indent_size = 4
```

### Benefits of this format

* Very readable
* Familiar and easy to pick up
* Difficult to mess up (syntax is very simple)

### Limitations

* File structure must be a list of sections (each with name and hash of properties)
* Only string datatypes natively supported for property values


## YAML format

### Benefits of this format

* Easily readable
* Spaces allowed in key and value names
* Many datatypes supported natively (boolean, numeric, strings, lists, hashes)

### Limitations

* May not be as familiar as INI or XML
* The top level structure uses an unordered hash unless `- ` is prepended to section names
* Section names using symbols (like `*`) must be surrounded by quotes

### Example file

```yaml
- root: true

- "*":
  - end of line: LF

- "*.py":
  - indent style: space
  - indent size: 4

- "*.html":
  - indent style: space
  - indent size: 2
```


## XML

### Benefits of this format

* XML parsers and formatters are readily available
* Format is flexible enough that drastic changes should not be necessary
* Probably somewhat familiar due to the widespread use of XML-based markup

### Limitations

* Not very human readable
* Cumbersome to create and modify due to often verbose syntax

### Example file

```xml
<setting root="true"/>
<pattern glob="*.py">
     <indentation style="space" size="4" tabwidth="4"/>
     <end_of_line style="LF"/>
</pattern>
```


## Other possible formats:

* [Lua](http://www.lua.org/)
* Struxt
* UDO
* [JSON](http://json.org/)
* [ArchieML](http://archieml.org/)
* [μSON](https://github.com/burningtree/uson)
