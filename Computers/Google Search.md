

# Syntax
## Searchbar
---
[Syntax Documentation](https://support.google.com/websearch/answer/2466433?hl=en)


## Address
---
[Advanced Search Tool](https://www.google.com/advanced_search)

- use `&` to separate commands
- assign values to commands w/ `=`
- whitespace is represented by `+`
`https://www.google.com/search?q=test+here&near=Dallas`

## Commands
### Core

| Use                        | URL      | Description / Example Values                 |
| -------------------------- | -------- | -------------------------------------------- |
| query                      | `q`      |                                              |
| original query             | `oq`     | typed user text before suggestion was chosen |
| session start              | `ei`     | date/time                                    |
| page load                  | `ved`    | date/time                                    |
| previous page load         | `sxsrf`  | date/time                                    |
| google web server redirect | `gws_rd` | e.g. `ssl` for secure socket layer           |


### Modifiers

| Use      | Syntax | Description / Example Values |
| -------- | ------ | ---------------------------- |
| language | `lr`   | `lang_de`                    |
| country  | `cr`   | `countryDE`                  |
| near     | `near` | city, state, or zip          |
