# Development Workflow
```yaml
# start development server with file watcher
hugo server --buildDrafts

# check for drafts
hugo list drafts
# build site in /public/ folder
hugo
```
### Linting
- This project uses `markdownlint` [CLI](https://github.com/igorshubovych/markdownlint-cli) tool to lint markdown files
```bash
markdownlint 'content/**/*.md' --fix
```
### Updating themes
```bash
# pull in any new changes from the theme
git submodule update --remote
```

# Deployment
This site is currently deployed via Github Actions to a repository Github Pages site on every push to the `main` branch