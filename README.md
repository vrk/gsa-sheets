# gsa-sheets
Node module for CRUD operations on a Google Server Account spreadsheet

# How to use

This library is distributed through npm:

```bash
$ npm install gsa-sheets
```

You construct a Google Sheets object by passing in the client email, private key, and spreadsheet id into the constructor:

```javascript
const googleSheets = require('gsa-sheets');
const sheet = googleSheets(client_email, private_key, spreadsheet_id);
```

- **CS193x students:** You can follow the [set-up instructions](http://web.stanford.edu/class/cs193x/homework/5-sheets) to understand and obtain the client email, key, and spreadsheet ID.

# Public methods
Here are the public methods of a `Sheet` object:

Method name | Description
--- | ---
`getRows()` | Returns the rows in the spreadsheet. This is an asynchronous function that returns a `Promise` that resolves to a JSON object with one property, `rows`. The value of `rows` is an array of the spreadsheet's row values, also stored in an array. For example, if you have a spreadsheet that looks like this: [screenshot](images/hw5-sheet-data.png), the value of "result" in a call to `const result = await sheet.getRows()` will look like this: [screenshot](images/hw5-getrows-json.png) .
`appendRow(newRow)` |  Adds the given row to the end of the spreadsheet. This is an asynchronous function takes an Array parameter, `newRow`. The array contains the list of values in order to add to the end of the spreadsheet. For example, a call to `sheet.appendRow([1, 2, 3])` would add a row where the first value was 1, the second value was 2, and the third value was 3.<br/><br/>`appendRow` returns a `Promise` that resolves to a result object, which will equal `{ success: "true" }` if the operation was successful, or `{ error: <error message> }` if the operation failed.
`deleteRow(rowIndex)` | Deletes the given row in the spreadsheet. The `rowIndex` indicates the 0-based row number of the spreadsheet, where the first row is 0, the second row is 1, etc.<br/><br/>`deleteRow` returns a `Promise` that resolves to a result object, which will equal `{ success: "true" }` if the operation was successful, or `{ error: <error message> }` if the operation failed.
`setRow(rowIndex,newRow)` | Sets a particular row in the spreadsheet to the given values. This is an asynchronous function takes two parameters, `rowIndex` and `newRow`. The `rowIndex` indicates the 0-based row number of the spreadsheet, where the first row is 0, the second row is 1, etc. The `newRow` is an array of values in the order that they should be set.<br/><br/>`setRow` returns a `Promise` that resolves to a result object, which will equal `{ success: "true" }` if the operation was successful, or `{ error: <error message> }` if the operation failed.
