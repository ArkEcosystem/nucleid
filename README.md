# NUCLeId Npm Universal Command Line Interface
A simple yet powerful package to use command line to use your package

Ever wanted to execute your favorite npm package in CLI wihtout having to deal with whatever super package cor custom use?

Ever wanted to embed a npm package into your favorite language using only CLI Shell?

Enter nucleid, the fast and easy way to call npm package within CLI:
- support input/output data in JSON
- you can pipe it
- dynamic package install (still to improve)


# Quickstart
## installation
`npm install -g nucleid`

## install your favorite package
`npm install -g arkjs`

## use it in cli
```
> nucleid --help

  Usage: nucleid [options] [arguments...]


  Options:

    -r, --require <package>   The package to require
    -e, --execute <function>  The function to execute
    -i, --install <package>   The package to install locally beforehand
    -u, --use <url>           the url of the snippet to use
    -p, --path <path>         the file to run
    --ijson                   Input argument is well formatted json that should be parsed as object
    --ojson                   Output result is object that should be well formatted json
    -h, --help                output usage information
```

```
> nucleid -r arkjs -e transaction.createTransaction "AN7BURQn5oqBRBADeWhmmUMJGQTy5Seey3" 1000000000 "" 🦄 --ojson
{"type":0,"amount":"1000000000","fee":10000000,"recipientId":"AN7BURQn5oqBRBADeWhmmUMJGQTy5Seey3","timestamp":12272383,"asset":{},"vendorField":"🦄","senderPublicKey":"037699680696ba0f746ee581d775b0ef13a8832fe2539be80eaabff154f3e3995d","signature":"3045022100a801b198bc8719bb953d32d6afbd19bb7df4dde4ec20fee1cb5ec4dd6fe41f4902201a27a7eef2220ca9474c70f57d56dbff81ef64c3e753e5daaad499da68d0b4f8","id":"64f8d7466ae6e7f11401affdbe4dfbd94414670c2ffbb83e8c43e11ac975557e"}
```

## embed in your own language
PHP does not have embed crypto lib simple to use in ark?

```php
<?php
$output = shell_exec('nucleid -r arkjs -e transaction.createTransaction "AN7BURQn5oqBRBADeWhmmUMJGQTy5Seey3" 1000000000 "" 🦄 --ojson');
echo "<h1>My signed transaction</h1><pre>$output</pre>";
?>
```

## wait! It is slightly more complex, i have put up a quick snippet to use the lib...
We got you covered:

```
> nucleid  "AN7BURQn5oqBRBADeWhmmUMJGQTy5Seey3" 1000000000 🦄  🦄  --use https://gist.githubusercontent.com/fix/4515e7cb37a2faec13878e2ce34d094d/raw/testsignature.js
```
or 
```
> nucleid  "AN7BURQn5oqBRBADeWhmmUMJGQTy5Seey3" 1000000000 🦄  🦄  --path ./test.js
```
