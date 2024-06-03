# heroku-buildpack-ffmpeg-latest

A Heroku buildpack for [pdo_snowflake](https://github.com/snowflakedb/pdo_snowflake).

The compiled extension is cached against the app's PHP version for super fast deploys. 

## Usage

Run the following from the heroku command line:

```
heroku buildpacks:add --index 1 https://github.com/morrislaptop/heroku-php-snowflake-buildpack.git
```

Note: This buildpack should be added after the PHP buildpack (by using `--index 1`),
since `phpize` is required to build the extension.
