# Development Workflow
```yaml
# start development server with file watcher
hugo server --buildDrafts
```

# Deployment
- make sure the `deployment.targets` section in `hugo.toml` is configured
1. Build the site
```
# build site in /public/ folder
hugo

# deploy to a target listed in hugo.toml config like an S3 bucket
hugo deploy --target=<target_name>
```