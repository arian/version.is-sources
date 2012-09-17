# Version.is sources repo

This repo contains the source files, which version.is is using to generate project versions.

## File structure

Each project has a .json file which contains data about how the versions are fetched.

The basic layout of a project file is as following:
```
<projectname>.json:
-------------------

{
  "project": "<projectname>",
  "handler": {}
  "meta": {}
}

```

The project name should be the same as the file name, apart from the json extension.

There is two standard ways to fetch data, specified by the handler object:
 - by GitHub tags
 - by package.json / component.json files in a GitHub repo.

GitHub tags are the best fit for most projects. The package.json/component.json files will be better for monitoring the latest development versions.

### handler object

The handler objects for jquery.json and jquery-dev.json looks like this:
```
jquery.json:
------------

"handler": {
  handler: "bytags",
  "source": "jquery/jquery"
}

jquery-dev.json:
----------------

"handler": {
  "handler": "byjsonfile",
  "source": "jquery/jquery",
  "file": "package.json"
}
```

The handler notes which handler should be invoked. The source parameter is noting the GitHub user/organization and the repo name. The file parameter is noting the json file that should be parsed for the version.

### meta object

The meta object can contain different kinds of meta data. Currently we support a `prettyname` string, that contains the formatted name, i.e. "jQuery" for the jquery project, and a `website` string containing the URL to the website for the project.

## Submitting your project

If you want to add your project to the list of monitored projects, please submit a pull request. We will make sure that it is working before accepting it, and will assist you in the process if needed.

Look at the existing projects for reference.

## Custom handlers

Some projects will have their own handlers. Examples being Google Chrome and Firefox browsers. Only selected projects will get this treatment. If you cannot make your project fit into the standard ways of version fetching get in touch with us.

Please be aware, that this service is not free for all projects and may be subject to billing. Only development time is billed, so do not hesitate to get in touch.