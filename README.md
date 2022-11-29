# com.matheusds365.vscode.yamlsyntax2json

Command to convert a YAML form of TMLanguage to JSON.

It supports variable replacement using the `{{variableName}}` syntax.

## Usage

Install with:

```
npm i -g com.matheusds365.vscode.yamlsyntax2json
```

Write a file `mylanguage.tmLanguage.yaml`:

```yaml
# tmLanguage
---
$schema: https://raw.githubusercontent.com/martinring/tmlanguage/master/tmlanguage.json
name: MyLanguageName
scopeName: source.mylang

variables:
  someVar: 'xxx'

patterns:
  - include: '#foo'

repository:
  foo:
    patterns: []
```

Then run:

```
yamlsyntax2json mylanguage.tmLanguage.yaml mylanguage.tmLanguage.json
```

The output looks like follows:

```json
{
    "$schema": "https://raw.githubusercontent.com/martinring/tmlanguage/master/tmlanguage.json",
    "name": "MyLanguageName",
    "patterns": [
        {
            "include": "#foo"
        }
    ],
    "repository": {
        "foo": {
            "patterns": []
        }
    },
    "scopeName": "source.mylang"
}
```