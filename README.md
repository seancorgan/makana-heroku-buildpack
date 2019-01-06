Add as a first buildpack in the chain. Set `PROJECT_PATH` environment variable to point to project root. It will be promoted to slug's root, everything else will be erased. Following buildpack (e.g. nodejs) will finish slug compilation.

**Disclaimer:** I may change the code without notice, so always pin to specific github version. Provided as is.

# How to use:
1. `heroku buildpacks:clear` if necessary
2. `heroku buildpacks:set https://github.com/SalesforceFoundation/makana-heroku-buildpack`
3. `heroku buildpacks:add heroku/nodejs` or whatever buildpack you need for your application
4. `heroku config:set PROJECT_PATH=projects/nodejs/frontend` pointing to what you want to be a project root.
5. Deploy your project to Heroku.

# How it works

The repository is filtered to just the `PROJECT_PATH` for the `develop` branch then the branch being built.
This is done to provide a usable diff for the `PROJECT_PATH`.
