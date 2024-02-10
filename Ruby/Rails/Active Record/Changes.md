An [[ActiveRecord|Active Record]] migration that is inherently reversible can be implemented as the method `def change` in a ruby class that inherits from `ActiveRecord::Migration`
### create_table
the create_table call takes `tableName:Symbol` and a block accepting one argument (henceforth `|t|`) and uses it to describe the changes to the table.
The following actions are supported:
- `t.column [column_name:Symbol] [data_type:SQLType] **<options>
	- There are shorthand methods for all default types (string, text, integer, bigint, float, double, and others)
	- `options` can be any or all of the following:
		- `comment [comment:String]` ignored by some database backends, supplies a comment for a column.
		- `default [value:ValueType]` defines a default value for a table.
		- `limit [width:integer]`. `width` refers to characters for a `string`, and bytes for `text|binary|blob|integer` columns. ignored by some backends.
		- `null [nullable:Boolean]` defines whether the column is nullable.
		- `precision [width:integer]` defines the precision of `decimal|numeric|datetime|time` columns. (e.g. 123.45 has a precision of 5)
		- `scale [decimal_width:integer]` defines the scale of a column, which is the number of digits after the decimal point. (e.g. 123.45 has a scale of 2.)
			- SQL standard defines `precision >= scale`.
				- postgres allows:
					- precision > 1
					- scale > 0
				- sqlite3 allows:
					- precision <= 16
		- `if_not_exists [toggle:Boolean]` should the table be created if it already exists? toggle=true prevents adding duplicate tables.
- `t.references [relation_name:Symbol], **<options>` (alias: `t.belongs_to`)
	- `relation_name` can be any symbol.
		- if it is the name (singular) of another table, `options.foreign_key` can be `true`.
	- options can contain any or all of the following:
		- `foreign_key {to_table: [table_name:Symbol]}` where `table_name` is a symbol matching the name of another table. 
		- `null: [nullable:Boolean = true]` where `nullable` matches the desired possibility for the value of this column to be NULL
		- `type: [type:SQLType = :bigint]` generally not used, available for situations where a foreign key is a type other than `bigint`.
		- `index: [indexed:Boolean = true]` where `indexed`represents whether this column will be indexed. 
### change_table
a call to change_table takes `[table_name:Symbol]` and a block accepting a single argument (henceforth `|t|`)
The block defines how the table columns will be changed by the migration.
The following actions are supported:
- `t.column` This behaves exactly the same as [[Changes#create_table|create_table]]'s `t.column` method.