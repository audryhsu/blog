This is the repository for my personal blog generated with Hugo.
## Development Workflow
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
npm run lint
```
### Updating themes
```bash
# pull in any new changes from the theme
git submodule update --remote
```

## Deployment
This site is currently deployed via GitHub Actions to a repository Github Pages site on every push to the `main` branch
