### Create/Update Fluxx Record

This Action will update a given Fluxx record if a Model Type and record id is specified. With no record id, it will create a new Fluxx record of the specified Model Type with the information provided.

It is up to you to ensure that all required fields are given valid values.

* **Input**
  * **Record ID**: Enter the id of the record to update, or leave blank to create a new record
  * **Model Group** (required): As there are so many model types to choose from, they have been broken down into four lists: Basic, Intermediate, Dynamic Models only, and All. This filters the Model Types shown in the Model Type field. "Basic" contains Document, Grant Request, Initiative, Organization, Program, Project, Request Report, Request Transaction, Sub Initiative, Sub Program, and User.
  * **Model Type** (requred): accepts model types in both styles: grant_request or GrantRequest. You must specify a Model Type before the Field List for Update/Create control will appear.
  * **Field List for Update/Create** (required)
    * This multiple-select control knows about all Core and Dynamic fields available for the Model Type you specify above.
    * The list of Core fields is followed by the list of Dynamic fields.
    * Each time you select a field, a new box appears below in order for you to specify another field. In this way, you first need to specify all the fields that you are going to update/create.
    * After you enter each field name, more information about that field appears in a list below the Field List

e.g.
```
Core field: model_theme_id
  • This is the ID of the theme that the record is using to render.
  • type: relation (ModelTheme) [links to API docs for ModelTheme on your Fluxx instance]
```

* Input (continued)
  * **Value List** (required)
    * For each of the fields in the Field List (above), you need to specify a value. Like the Field List, each time you fill in a value a new box appears below.
    * You must have the same number of boxes in the Field List as you have boxes in the Value List. The first box in the Field List matches with the first box in the Value List, the second box in the Field List matches with the second box in the Value List, etc.
    * For boolean values, use 1 for true and 0 for false.
    * For foreign keys (most fields that end in "_id"), either hard-code an id, or you may need to perform another search to retrieve the required id. To set the id to null, leave the text field blank.
    * Multi-attribute values (select controls that allow more than one value, and/or percentage) can be specified using a [special syntax](../Special/Multi_Value_Fields.md) that allows you to _remove_ existing selections and/or add selections. It cannot create Model Attribute Values that do not already exist in the system.