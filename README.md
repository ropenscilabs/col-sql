Catalogue of Life to SQL
========================

COL taxonomy as SQLite DB

__TLDR:__ The backbone as sqlite is up at <https://s3-us-west-2.amazonaws.com/taxize-dbs/col.sqlite>

## how we do

* download COL taxonomy from <http://www.gbif.org/dataset/d7dddbf4-2cf0-4f39-9b2a-bb099caae36c> as Darwin Core Archive
* unzip
* create sqlite DB `col.sqlite`
* import data files into sqlite DB
* upload `col.sqlite` to Amazon S3

## Usage

download

```
git clone https://github.com/ropensci/col-sql.git
cd col-sql
```

bundle it

```
bundle install
```

```
rake --tasks
```

```
rake all    # get data, convert to sql, upload to amazon s3
rake clean  # delete files not needed
rake fetch  # get and unzip data
rake s3     # upload database to s3
rake sql    # create sql database
```

`rake all` does all the things

Or, you can do each separately with `rake fetch` then `rake sql`, then `rake s3`, then `rake clean`

### Env vars

`rake s3` requires AWS keys. If you want to upload to AWS, make sure you have env vars with the names `AWS_S3_WRITE_ACCESS_KEY` and `AWS_S3_WRITE_SECRET_KEY`

## COL sqlite file

<https://taxize-dbs.s3-us-west-2.amazonaws.com/col.sqlite>

## COL taxonomy citation:

> Roskov Y., Ower G., Orrell T., Nicolson D., Bailly N., Kirk P.M., Bourgoin T., DeWalt R.E., Decock W., Nieukerken E. van, Zarucchi J., Penev L., eds. (2019). Species 2000 & ITIS Catalogue of Life, 2019 Annual Checklist. Digital resource at www.catalogueoflife.org/annual-checklist/2019. Species 2000: Naturalis, Leiden, the Netherlands. ISSN 2405-884X.

See also <http://www.catalogueoflife.org/col/info/cite> for how to cite COL individual databases, and more.
