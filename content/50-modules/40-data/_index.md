+++
title = "Data"
weight = 40
description = "N2 data nodes"
date = "2025-12-12T01:46:39.298Z"
+++

This module offers a suite of configurable workflow nodes designed to simplify data automation within Odoo. These nodes handle common data operations such as reading, transforming, validating, and writing records, reducing the need for custom code.

## Dependencies
This module depends on the following modules *:
- `n2`
- `n2_ui`

*Built-in modules not listed

## Python Requirement
This module requires the following Python package:
- `pandas`

## ActiveDataNode
Retrieves the current recordset provided by record-related triggers.
Use this node when subsequent workflow steps depend on the record that initiated the automation.

**Parameters**
- `key` {{% badge style="raw" %}}Raw{{% /badge %}}
- `selected_fields` {{% badge style="raw" %}}Raw{{% /badge %}}

The `key` is used as key of the result dict of the node.

## ArchiveDataNode
Represents the action_archive method of Odoo models.
This node is used to archive records from the database as part of an automated process.

**Parameters**
- `ids` {{% badge style="eval" %}}Eval{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}

The `ids` is evaluated to search and archive recordset of the related `model`.

## BrowseDataNode
Acts as a bridge to fetch records from the database, representing the browse method in Odoo models.
Used in combination with `DataGroupNode` or `DataNode` to define precisely what data should be examined.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `reference_field` {{% badge style="raw" %}}Raw{{% /badge %}}
- `reference_values` {{% badge style="eval" %}}Eval{{% /badge %}}

The `reference_field` and `reference_values` are used as domain filter to browse `model`

## CreateDataNode
Represents the create method of Odoo models.
Use this node to generate new records based on workflow inputs or results from other nodes.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `fields` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="eval" %}}Eval{{% /badge %}}

The `field['value']` is evaluated with current context, active record and lookup function of the connected `LookupNode` while `field['name']` is used as is to create recordset of the `model`.

## DataGroupNode
Retrieves grouped data (e.g., aggregated or structured recordsets).
Paired with BrowseDataNode to define grouping logic when collecting related records.

**Parameters**
- `key` {{% badge style="raw" %}}Raw{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `selected_fields`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `aggregate_function`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `group_field`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `datetime_granularity`  {{% badge style="raw" %}}Raw{{% /badge %}}
- `output_type`  {{% badge style="raw" %}}Raw{{% /badge %}}

## DataNode
Retrieves data or recordsets.
When combined with BrowseDataNode, it is used to fetch specific fields or related model data.

**Parameters**
- `key` {{% badge style="raw" %}}Raw{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `selected_fields`  {{% badge style="raw" %}}Raw{{% /badge %}}

The `selected_fields` are used to determine the values to be returned when querying the `model`.
The `key` is used as the key of the result dict.

## DomainFilterNode
Adds domain filters to data retrieval operations.
Ideal for narrowing recordsets when using `DataGroupNode` or `DataNode`, enabling queries such as “open invoices only” or “records created this year.”

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `domain` {{% badge style="liteval" %}}LitEval{{% /badge %}}

`domain` is used as additional domain filter for the `model`.

## DynamicDateFilterNode
Provides dynamic, date-driven filtering—for example, retrieving records from the current week, month, or year.
Useful in reports, KPIs, or scheduled workflows that operate relative to the current date.

**Parameters**
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `dynamic_date_field` {{% badge style="raw" %}}Raw{{% /badge %}}
- `dynamic_date_interval` {{% badge style="raw" %}}Raw{{% /badge %}}

`dynamic_date_interval` and `dynamic_date_field` is used to create additional domain filter for the `model`.
```python
domain = (<dynamic_date_field> >= start_of(now, <dynamic_date_interval>)) and (<dynamic_date_field> <= end_of(now, <dynamic_date_interval>))
```

## LookupNode
Supplies lookup data during record creation or modification.

**Parameters**
- `key` {{% badge style="raw" %}}Raw{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `lookup_field` {{% badge style="raw" %}}Raw{{% /badge %}}
- `value_field` {{% badge style="raw" %}}Raw{{% /badge %}}

The `lookup_field` is used to create lookup function of the `model`. The value of the `value_field` is returned when calling the lookup function.

The `key` is as the key to access the lookup function.

Expression to use the lookup function:
```python
lookup[<key>](<lookup_value>)
```

This expression creates a domain used to find the related recordset:
```python
<lookup_field> = <lookup_value>
```
The lookup function returns the value of the `value_field` if exists, otherwise the lookup function returns `None`

## UpdateActiveDataNode
Updates the current recordset provided by record-triggered workflows.

**Parameters**
- `fields` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="eval" %}}Eval{{% /badge %}}

`fields` is a dictionary:
```python
{
    `value`: str,
    `name`: str
}
```

The `field['value']` is evaluated with current context and active record while `field['name']` is used as is to update the active record of the `active_model` in the current context.

## UpdateDataNode
Represents the write method of Odoo models.

**Parameters**
- `ids` {{% badge style="eval" %}}Eval{{% /badge %}}
- `model` {{% badge style="raw" %}}Raw{{% /badge %}}
- `fields` {{% badge style="raw" %}}Raw{{% /badge %}} {{% badge style="eval" %}}Eval{{% /badge %}}

`fields` is a dictionary:
```python
{
    `value`: str,
    `name`: str
}
```
The `field['value']` is evaluated with current context, active record and lookup function of the connected `LookupNode` while `field['name']` is used as is to update the record of the `model`.
