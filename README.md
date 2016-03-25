<a name="flatly"></a>
## flatly
flatly is a simple flat file JSON db system.IMPORTANT: flatly is under active development and is not considered production ready

**Kind**: global class  

* [flatly](#flatly)
    * [new flatly()](#new_flatly_new)
    * [.dbInfo()](#flatly+dbInfo) ⇒ <code>Object</code>
    * [.getSchema()](#flatly+getSchema) ⇒ <code>Array.&lt;string&gt;</code>
    * [.tables()](#flatly+tables) ⇒ <code>Array</code>
    * [.getTable(tblName)](#flatly+getTable) ⇒ <code>Object</code>
    * [.findOne(criteria)](#flatly+findOne) ⇒ <code>Object</code>
    * [.findAll(criteria)](#flatly+findAll) ⇒ <code>\*</code>
    * [.use(options)](#flatly+use) ⇒ <code>[flatly](#flatly)</code>
    * [.refreshTable(tblName)](#flatly+refreshTable) ⇒ <code>object</code>
    * [.save(options, [callback])](#flatly+save) ⇒ <code>[flatly](#flatly)</code>
    * [.checkExists(tblName, column, value)](#flatly+checkExists) ⇒ <code>boolean</code>
    * [.insert(row, tblName)](#flatly+insert) ⇒ <code>[flatly](#flatly)</code>
    * [.update(rowData, matchBy, tblName)](#flatly+update) ⇒ <code>[flatly](#flatly)</code>

<a name="new_flatly_new"></a>
### new flatly()
flatly class contains the entire flatly api

<a name="flatly+dbInfo"></a>
### flatly.dbInfo() ⇒ <code>Object</code>
Returns currently selected database name and table names

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Returns**: <code>Object</code> - An object with the database name, table names and table count  
<a name="flatly+getSchema"></a>
### flatly.getSchema() ⇒ <code>Array.&lt;string&gt;</code>
Returns the schema of the currently selected DB

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Example**  
```js
console.log(flatly.getSchema()); // -> ['table1', 'table2', 'table3']
```
<a name="flatly+tables"></a>
### flatly.tables() ⇒ <code>Array</code>
Returns a deep clone of the tables array

**Kind**: instance method of <code>[flatly](#flatly)</code>  
<a name="flatly+getTable"></a>
### flatly.getTable(tblName) ⇒ <code>Object</code>
Returns an object representing the table requested. Use [findOne](#flatly+findOne) or [findAll](#flatly+findAll) for querying table contents

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Returns**: <code>Object</code> - An object representing the requested table  

| Param | Type | Description |
| --- | --- | --- |
| tblName | <code>String</code> | The name of the table to be returned |

<a name="flatly+findOne"></a>
### flatly.findOne(criteria) ⇒ <code>Object</code>
Returns a row from the specified table

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Returns**: <code>Object</code> - A row object  
**Params**: <code>String</code> criteria.where.column The name of the column to search  
**Params**: <code>number\|String</code> criteria.where.equals The value to search the column for  

| Param | Type | Description |
| --- | --- | --- |
| criteria | <code>Object</code> | An options object with the search details |
| criteria.from | <code>String</code> | The name of the table to search |
| criteria.where | <code>Object</code> | An object containing the column and value criterion |

<a name="flatly+findAll"></a>
### flatly.findAll(criteria) ⇒ <code>\*</code>
Returns all rows that match the criteria object

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Params**: <code>String</code> criteria.where.column The name of the column to search  
**Params**: <code>number\|String</code> criteria.where.equals The value to search the column for  

| Param | Type | Description |
| --- | --- | --- |
| criteria | <code>Object</code> | An options object with the search details |
| criteria.from | <code>String</code> | The name of the table to search |
| criteria.where | <code>Object</code> | An object containing the column and value criterion |

<a name="flatly+use"></a>
### flatly.use(options) ⇒ <code>[flatly](#flatly)</code>
Loads a database from the specified filepath

**Kind**: instance method of <code>[flatly](#flatly)</code>  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> |  |
| options.name | <code>String</code> | Specify a name for the database |
| options.src | <code>String</code> | A path to the required data |

<a name="flatly+refreshTable"></a>
### flatly.refreshTable(tblName) ⇒ <code>object</code>
Refresh table from disk

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Returns**: <code>object</code> - Table  

| Param | Type | Description |
| --- | --- | --- |
| tblName | <code>string</code> | Table name to refresh |

<a name="flatly+save"></a>
### flatly.save(options, [callback]) ⇒ <code>[flatly](#flatly)</code>
Save table data to disk. Remove flatly metadata before saving.

**Kind**: instance method of <code>[flatly](#flatly)</code>  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| options | <code>Object</code> |  |  |
| options.table | <code>string</code> |  | The table to save |
| [options.overwrite] |  | <code>false</code> | Overwrite the existing table? |
| [options.async] | <code>boolean</code> | <code>false</code> | Sync/Async Execution. Defaults to Sync |
| [callback] | <code>function</code> |  | The callback to execute if we're working asynchronously |

<a name="flatly+checkExists"></a>
### flatly.checkExists(tblName, column, value) ⇒ <code>boolean</code>
Check if a record (row) exists within a given table

**Kind**: instance method of <code>[flatly](#flatly)</code>  
**Returns**: <code>boolean</code> - Returns {true} if the value is found {false} otherwise  

| Param | Type | Description |
| --- | --- | --- |
| tblName | <code>string</code> | The name of the table to check |
| column | <code>string</code> | The column to search |
| value | <code>\*</code> | The value to search for |

**Example**  
```js
if(flatly.checkExists('table1', 'id', 1)) { //do something }
```
<a name="flatly+insert"></a>
### flatly.insert(row, tblName) ⇒ <code>[flatly](#flatly)</code>
Insert a row into a table

**Kind**: instance method of <code>[flatly](#flatly)</code>  

| Param | Type | Description |
| --- | --- | --- |
| row | <code>object</code> | Row object to insert |
| tblName | <code>string</code> | Name of the table to insert into |

<a name="flatly+update"></a>
### flatly.update(rowData, matchBy, tblName) ⇒ <code>[flatly](#flatly)</code>
Update an existing table row

**Kind**: instance method of <code>[flatly](#flatly)</code>  

| Param | Type | Description |
| --- | --- | --- |
| rowData | <code>Object</code> | An object representing a row of the target table |
| matchBy | <code>String</code> | The key to use to match rowData to an existing row in the table |
| tblName | <code>String</code> | The target table name |

**Example**  
```js
flatly.update({     id: 6,     name: Michael Flatly }, 'id', 'customers');
```
