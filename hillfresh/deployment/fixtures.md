#

## Fixtures

1. Isolate docTypes to change/ Alter or that are altered
2. To create fixtures (changes made in the docTypes), use the following process.

```bash
bench --site [your-site] export-fixtures

```
After the fixtures are exported and the changes need to be pulled to the local branch, proceed and push the code to the server...

- On the server, you can pull changes to the custom docType by using, the following command
  
```bash

bench --site [test-site] import-fixtures --path [path-to-fixtures] --app [your-custom-app]
```
