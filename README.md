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

## PHP

```php
  $account = "<account_name>";
  $user = "<user_name>";
  $password = "<password>";
  $warehouse = "<warehouse_name>";
  $database = "<database_name>";
  $schema = "<schema_name>";

  $dbh = new PDO("snowflake:account=$account;warehouse=$warehouse;database=$database;schema=$schema", $user, $password);
  $dbh->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
  echo "Connected\n";

  $sth = $dbh->query("select 1234");
  while ($row=$sth->fetch(PDO::FETCH_NUM)) {
      echo "RESULT: " . $row[0] . "\n";
  }
  $dbh = null;
  echo "OK\n";
```
