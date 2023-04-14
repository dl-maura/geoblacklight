# UMass Amherst Portal for Geospatial Data (UMAP GeoData)
UMass Amherst's [GeoBlacklight](https://geoblacklight.org) instance.

### Release Version
UMAP GeoData v1.0.0 / GeoBlacklight v4.0.0

## Installation

### Dependencies

View the full GeoBlacklight release and technology dependency matrix here: [Releases](https://geoblacklight.org/docs/overview/releases/).

* [Ruby](https://www.ruby-lang.org/en/) 3.2.0
* [Rails](https://rubyonrails.org) 7.0.4
* [Java](https://www.java.com/en/) 8 or greater (Solr)
* [Node.js](https://nodejs.org/en/) (yarn)
* [MySQL](https://dev.mysql.com/downloads/mysql/) v8

### Setup

[GoRails](https://gorails.com/setup) has great Ruby on Rails setup instructions for macOS, Ubuntu, and Windows.

If using Homebrew, install Java via:

```bash
brew install java
```

### Clone the Project

```bash
cd <your project directory>
git clone git@github.com:/umass-gis/geoblacklight.git
```

### Configuration

Duplicate the .example files in the project and remove the .example string from each of their filename. Configure each file as necessary, or keep the default values.

```bash
cp .example.env.development .env.development  
cp .example.env.test .env.test
```

### Bundle RubyGems

```bash
bundle install
```

### Yarn Packages

```bash
yarn install
```

### Create the Database

```bash
bin/rails db:create RAILS_ENV=development
```

### Run the Database Migrations

```bash
bin/rails db:migrate RAILS_ENV=development
```

### Run the Application

The rake task below will spin up Solr, index the test fixture documents, and start the default Rails web server.

```bash
bundle exec rake umass:server
```

* View the application at [http://localhost:3000](http://localhost:3000)
* View the Solr admin panel at [http://localhost:8983](http://localhost:8983)

### Run the Test Suite

Stop any instances of GeoBlacklight before running this command.

```bash
RAILS_ENV=test bundle exec rake ci
```

### Rake Tasks for Solr

Delete all data from the Solr index

```bash
bundle exec rake umass:index:delete_all
```

Index just the UMass test fixtures

```bash
bundle exec rake rake umass:index:umass
```
