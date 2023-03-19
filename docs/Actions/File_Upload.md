### File Upload

This action creates a new ModelDocument based on a document output from a previous Zap trigger or action (e.g. a mail attachment from an email received in Gmail or Exchange Mail, or from a previous Fluxx action), or from a URL. If you have a static file that you want to upload, you will need to upload it to a web site/service in order to get a URL for it.

All files uploaded through this Action must be attached to a Model Type and Model Id, e.g. attached to GrantRequest with id 12345. It is recommended that you also specify a Doc Label (often _default_) and a Model Document Type by id.

* **Input**
  * **Filename including extension** (required)
  * **File** (required). The file field acts differently depending on what data is mapped to it:
    * Text: Zapier will turn text into a .txt file and that file will be uploaded to the app.
    * URL: if you enter a URL, Zapier will try to load the data available at that address and upload it as a file.
    * File: if a file is mapped from the trigger or another action, Zapier will upload it.
  * **Doc Label**: Label for document so that different Document components can pick different sets of documents, by label. Default: _default_
  * **Content (MIME) Type** (required). This is usually available from the trigger or action that provided the file. e.g.
    * text/plain
    * application/pdf
    * image/png
    * image/jpeg
    * application/msword
    * application/vnd.openxmlformats-officedocument.wordprocessingml.document
    * text/csv
    * application/vnd.ms-excel
    * application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
    * application/vnd.ms-powerpoint
    * application/vnd.openxmlformats-officedocument.presentationml.presentation
    * application/zip
    * audio/mpeg
    * video/mp4
    * video/mpeg
  * **Model Type** (required): Can be in snake_case or CamelCase (e.g. grant_request or GrantRequest). This is the type of model to which the document will be attached. All new documents must be attached to a model.
  * **Related Model Id** (required): the Id of the model to which the document will be attached.
  * **Model Document Type**: This dynamic dropdown queries Fluxx for the ModelDocumentTypes available for the Model Type chosen. The resultant ModelDocument will be labelled with this Model Document Type. The list is the same as what you would find listed in the Fluxx Admin panel on Card Documents => {{ Model Type }} => Documents tab
  * **Model Document Sub Type**: If the selected Model Document Type has sub types, this selector will allow you to select which one use.
  * **"name segment for user search below"**: This is a helper field for the User Id selector. Fill in this field with the name (or part of the name) of the "created_by" user, before searching with the selector below. This helps to trim down the number of results shown. NOTE: you must select a user below, after filling in this box.
  * **Created By Id** (required): enter the User id to use for the Created By Id. You may be able to may a user id from a previous step, _or_ use the box above to help narrow down the Id search.
* **Output**
  * id (the ModelDocument Id)
  * document_type (returns "file")
  * doc_label (e.g. "default")
  * document_content_type (the MIME type)
  * document_file_name
  * model_document_type_id.id
  * model_document_type_id.name
  * model_document_sub_type_id.id
  * model_document_sub_type_id.name
  * updated_by.id
  * updated_by.full_name
  * created_by.id
  * created_by.full_name
  * document_file_size (in Bytes)
