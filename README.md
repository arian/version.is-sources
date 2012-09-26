# Version.is sources repo

This repo contains the source files, which version.is is using to generate project versions.

Version.is repo is available at [gustavnikolaj/version.is](https://github.com/gustavnikolaj/version.is).

## File structure

Each project has a .yaml file which contains data about how the versions are fetched.

There is two standard ways to fetch data, specified by the handler object:
 - by GitHub tags
 - by package.json / component.json files in a GitHub repo.

GitHub tags are the best fit for most projects. The package.json/component.json files will be better for monitoring the latest development versions.

## Submitting your project

If you want to add your project to the list of monitored projects, please submit a pull request. We will make sure that it is working before accepting it, and will assist you in the process if needed.

Look at the existing projects for reference.

## Custom handlers

Some projects will have their own handlers. Examples being Google Chrome and Firefox browsers. Only selected projects will get this treatment. If you cannot make your project fit into the standard ways of version fetching get in touch with us.

Please be aware, that this service is not free for all projects and may be subject to billing. Only development time is billed, so do not hesitate to get in touch.