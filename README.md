# markdown-add-files
github action to add in files as examples to markdown files 

this action finds .md.template files and replaces `+++file: ./app.tsx` with the code from that file. it then takes that .md.template file and creates a file with just .md

## example 
this is a very simple action that simple builds the template files and then pushes the built markdown to the repo

```yml
name: generate markdown

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - uses: nwylynko/markdown-add-files@v1
      - uses: EndBug/add-and-commit@v4
        with:
          author_name: README builder
          message: 'Updated Readme'
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
