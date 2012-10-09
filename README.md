# Version.is Sources Repo

This repo contains the source files, which version.is is using to generate project versions.

Version.is repo is available at [gustavnikolaj/version.is](https://github.com/gustavnikolaj/version.is).

## File Structure

Each project has a .yaml file which contains data about how the versions are fetched.

There is two standard ways to fetch data, specified by the handler object:
 - by GitHub tags
 - by package.json / component.json files in a GitHub repo.

GitHub tags are the best fit for most projects. The package.json/component.json files will be better for monitoring the latest development versions.

## Submitting your Project

If you want to add your project to the list of monitored projects, please submit a pull request. We will make sure that it is working before accepting it, and will assist you in the process if needed. Take a look at the existing projects for reference.

The conventions for file names is, that they must only contain characters `a-z` and `-` dash. Letters should be converted to lowercase and punctuation and spaces should be replaced by dashes. The file extension should be `yaml`.

The contents of the file should be valid yaml. Each project branch should have their own yaml object. The first object should be the base branch, and the name of that should correspond to the filename. Additional branches, should be named the same as the base-branch, with an addition of a branch name seperated by a dash. If the project was jQuery, it would have the filename `jquery.yaml` and two yaml objects in the file, `jquery` and `jquery-dev`. 

Each yaml object have some required properties; `name` and `website`, which should be pretty obvious.

Additionally, each yaml object has a object named `handler`. This object specifies how and where to fetch version data. There is custom handlers for some projects, but those will generally not be interesting, if you are submitting it yourself. The handler has one universal property, `type` that specifies which method will be used to fetch version data.

### Handlers

#### bytags

This handler is invoked by setting `type: bytags` as a property on the handler object. It has only one required property, which is `repo`. It works by fetching version data from tags on a GitHub repo. A handler object for jQuery using the tags on their [GitHub repo](http://github.com/jquery/jquery "jQuery GitHub repo") would look like this:

```yaml
handler:
  type: bytags
  repo: jquery/jquery
```

#### by jsonfile

This handler is invoked by setting `type: byjsonfile` as a property on the handler object. It has two required properties, `repo` and `file`. It works by fetching version data from a json file in a GitHub repo. It is intended to be used with `package.json` and `component.json` files, but it should work with all jsonfiles that has an object with a `version` property, as that is what it tries to parse.

A handler object for the development branch of jQuery using the `package.json` file in their [GitHub repo](http://github.com/jquery/jquery "jQuery GitHub repo") would look like this:

```yaml
handler:
  type: byjsonfile
  repo: jquery/jquery
  file: package.json
```

#### Custom Handlers

Some projects will have their own handlers. Examples being Google Chrome and Firefox browsers. Only selected projects will get this treatment. If you cannot make your project fit into the standard ways of version fetching get in touch with us.

Please be aware, that this service is not free and may be subject to billing. Only development time is billed, so do not hesitate to get in touch.

Some projects may be of such great significance that we have added custom handlers for them.

## Suggestions

If you have suggestions to the project, please refer to the project repo at [gustavnikolaj/version.is](https://github.com/gustavnikolaj/version.is).

If you feel that there is need for another basic handler type, please get in touch.
