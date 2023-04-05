### Search for a List of Fluxx Records (Line Item Support)

There may be times when you need to load in a set of Fluxx records related to a previous item, perhaps to access their values or to update them in some way. This action allows you to perform a Fluxx search based on a SQL-like query. If there are values from the Trigger or a previous Action that you need to use in the query, you can sub these values into the text box where appropriate.

The list of items is returned as a Zapier "Line Item" set. You can use the "Looping by Zapier" action to loop through the line items, repeating any subsequent Zap steps for each of the items in the Line Item set. Note that each Action completed in a loop iteration counts against your Zapier Tasks count.

* **Input**
  * **SQL input**: see [_SQL Support_](../Special/SQL_Support.md) e.g. `SELECT id, name, nz_charities_number FROM Organization WHERE postal_code = "4500"`
    * Don't forget that you can sub values from previous steps into the SQL string e.g. ... `WHERE postal_code = "[[1. Postal Code: 4500]]"`
* **Output**
```
results
  1:
    id: 105
    model_type: organization
    fields:
      id: 105
      name: Support Group for Those Bereaved by Suicide
      nz_charities_number: null
      (all other requested fields appear here)
  2:
    id: 12
    model_type: organization
    fields:
      id: 12
      name: Central Kindergarten
      nz_charities_number: null
      (all other requested fields appear here)
```

* **Output with MAVs**
```
results
  1:
    id: 21553552
    model_type: grant_request
    fields:
      id: 21553552
      grant_or_request_id: GC-2006-34227
      app_specific_focus_level_of_need_and_age: true
      program_organization_id.id: 10261982
      program_organization_id.org_deprivation_reach:  #NB: this is a single select
        1:
          id: 10097888
          desc: Community Deprivation
          val: Community Deprivation
      program_organization_id.org_deprivation.add_list: §add§New Plymouth District§Blagdon | Moturoa | Lynmouth (8)
      program_organization_id.org_deprivation.add_list_by_id: §add_by_id§10097725
      program_organization_id.org_deprivation.line_items:
        1.
          id: 10097725
          percent: null
          path: §New Plymouth District§Blagdon | Moturoa | Lynmouth (8)
          value: Blagdon | Moturoa | Lynmouth (8)
          description: Blagdon | Moturoa | Lynmouth (8)
  2:
```

** Output from _Select_ Fields**

Values from Select fields are output from FCE actions in several different formats for maximum flexibility.

1. **Single Select** controls are output in an object in an array of size 1, with their MAV id, value and description.

e.g. Viewed in the Test output from a Zapier Action:

```
reach:
  1:
    id: 10097888
    desc: Community Deprivation
    val: Community Deprivation
```

e.g. Viewed in the input to subsequent actions:

```
Fields Reach Id: 10097888
Fields Reach Val: Community Deprivation
Fields Reach Desc: Community Deprivation
```

2. **Multi-value Select** controls (e.g. checklists, Select-Transfers, or Hierarchical Dropdowns) are output in the following ways:
     * As the field name appended with ".add_list": in the format used by the Create/Update Fluxx Record MAV format (see [here](../Special/Multi_Value_Fields.md)). This allows you to feed the output of a single or multi item select into the Create/Update Fluxx Record, and allow it to recreate the same Model Attribute Values for a given field.
       * e.g. ```§add§New Plymouth District§Blagdon | Moturoa | Lynmouth (8)```
     * As the field name appended with ".add_list_by_id": similar to (b) except uses the MAV id.
       * e.g. ```§add_by_id§10097725```
     * As Zapier Line Items, with the field name appended with ".line_items": an array of objects, each containing the id, percent, path to the final value (delimited with the § character), value and description of the final value.

e.g. Viewed in the Test output from a Zapier Action:
```
communities.add_list:
    §add/60§California§Los Angeles
    §add/40§California§San Francisco
communities.add_list_by_id:
    §add_by_id/60§9978168
    §add_by_id/40§9978170
communities.line_items:
  1:
    path: §California§Los Angeles
    id: 9978168
    val: Los Angeles
    percent: 60
    desc: Los Angeles
  2:
    path: §California§San Francisco
    id: 9978170
    val: San Francisco
    percent: 40
    desc: San Francisco
```

e.g. Viewed in the input to subsequent actions:

```
Fields Communities Add List: §add/60§California§Los Angeles\n§add/40§California§San Francisco
Fields Communities Add List By Id: §add_by_id/60§9978168\n§add/40§9978170
Fields Communities Line Items Desc: Los Angeles, San Francisco
Fields Communities Line Items Id: 9978168, 9978170
Fields Communities Line Items Path: §California§Los Angeles, §California§San Francisco
Fields Communities Line Items Percent: 60, 40
Fields Communities Line Items Val: Los Angeles, San Francisco
```

Note that the Add List and Add List By Id values may contain newlines and can be used as input to the FCE "Create/Update Fluxx Record" Action, but the Line Items are comma-separated lists that are treated as  Zapier Line items (see [docs](https://zapier.com/blog/formatter-line-item-automation/)). See [here](../Special/Multi_Value_Fields.md) for more information about FCE's handling of multi-attribute fields.
