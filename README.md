# tablesort.js

Tablesort is a small & simple sorting component for tables written in Javascript. It has no dependencies and should have no interference with other libraries.

## Basic usage

``` html
<script src='tablesort.min.js'></script>
<script>
  new Tablesort(document.getElementById('table-id'));
</script>
```
## Sort Types

* strings
* numbers
* currency
* Basic dates in `dd/mm/yy` or `dd-mm-yy` format. Years can be 4 digits. Days and Months can be 1 or 2 digits.

## Additional options

__Ascending/Descending__
You can pass in options as a second parameter. Currently one option is supported: `descending: true`. By default, sort is set to ascending.

``` html
new Tablesort(document.getElementById('table-id'), {
  descending: true
});
```

__Exclude columns__
For columns that do not require sorting, you can add a class of `no-sort` to a columns `th` element.
``` html
<th class='no-sort'>Name</th>
```

__Refresh sort on appended data__
Tablesort supports sorting when new data has been added. Simply call the refresh method.

``` js
var table = document.getElementById('table-id');
var sort = new Tablesort(table);

// Make some Ajax request to fetch new data and on success:
sort.refresh();
```

[See homepage for example](http://tristen.ca/tablesort/demo/#refresh)

## Ender support
Add `tablesort` as an internal chain method to your [Ender](http://ender.no.de) compilation.

``` shell
$ ender add tablesort
```

Use it:

``` js
$('.table').tablesort();
```

## Default style
Add the styling below to your CSS or roll with your own.

``` css
th.sort-header {
  cursor:pointer;
  }
th.sort-header::-moz-selection,
th.sort-header::selection {
  background:transparent;
  }
table th.sort-header:after {
  content:'';
  float:right;
  margin-top:7px;
  border-width:0 4px 4px;
  border-style:solid;
  border-color:#404040 transparent;
  visibility:hidden;
  }
table th.sort-header:hover:after {
  visibility:visible;
  }
table th.sort-up:after,
table th.sort-down:after,
table th.sort-down:hover:after {
  visibility:visible;
  opacity:0.4;
  }
table th.sort-up:after {
  border-bottom:none;
  border-width:4px 4px 0;
  }
```

## Building

Developers can rebuild the minified library by running:

``` bash
  npm install --dev
  make
```

## TODOs

* Tests
* Pass in an options object to:
  - Choose which row to begin sorting on.
  - EventListener to rebuild the table in Ender.

## Licence

MIT

## Bugs?

[Create an issue](https://github.com/tristen/tablesort/issues)

