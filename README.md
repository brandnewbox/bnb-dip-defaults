# BNB Dip Defaults

Shared dip configuration defaults for Brand New Box team members.

## Background

BNB uses dip to consistently act inside our docker containers. A lot of those commands are the same across all projects. This project maintains a set of shared dip commands that we can all use.

## How to use

Install [dip](https://github.com/bibendi/dip).

Clone this repository onto your machine. Location does not matter.

Create a symbolic link to this projects `dip.yml` file in your home directory (or some other high level directory that contains all of your BNB projects).

```
cd ~
ln -s /path/to/bnb-dip-defaults/dip.yml ~/dip.yml
```

Now, when you are in any sub-directory, dip will search up and find this shared `dip.yml` file.

When you are wanting to add additional commands to a specific repository, create a `dip.override.yml` inside the repository and dip will merge that in with these global defaults.

## Update

You can get the latest and greatest BNB Dip Defaults by pulling the latest from GitHub.

## Caveats

In order to get support for both `development` and `test` environments, there are a few things you must "under-specify":

### Database URL

Your environment variable should set the database URL _without_ the database name. Rails will use the name specified in your `database.yml` config to determine the database name.

```
DATABASE_URL=postgis://postgres:password@postgres:5432
```

```yaml
default: &default
  adapter: postgis
  encoding: unicode
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  schema_search_path: public

development:
  <<: *default
  database: rosetta_development

test:
  <<: *default
  database: rosetta_test
```

### RAILS_ENV

Do not specify `RAILS_ENV=development` in your `.docker-development-vars`. Rails will figure this out by default. Doing so will give bundler the freedom to install both development AND test gems.