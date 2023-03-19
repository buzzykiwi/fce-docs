### File Download

* **Input**
  * **id**: the Id of the ModelDocument you want to download
* **Output** 
  * **id**
  * **file** (type: file, can be used as input in any Zap action that takes a file as input)
  * **document_content_type**
  * **document_file_name**
  * **created_at**
  * **created_by_id.id**
  * **created_by_id.full_name**
  * **updated_at**
  * **updated_by_id.id**
  * **updated_by_id.full_name**
  * **doc_label**
  * **document_file_size**
  * **document_updated_at**
  * **original_file_name**
  * **model_document_type_id.id**
  * **model_document_type_id.name**
  * **document_type**
  * **document_text**
  * **documentable_type**
  * **documentable_id**
  * **model_document_template_id.id**
  * **model_document_template_id.description**
* **Notes**
  * The file output uses Zapier's dehydrate function, which temporarily hosts the file on a Zapier server
  * Occasionally, this action seems to truncate the file before passing it on. Please report this if it happens.
  * If you require any other fields, e.g. Dynamic Fields, you can retrieve these with the Action "Search for a Single Fluxx Record" or the Search "Search for Record". Both options allow you to specify arbitrary field names to retrieve, but neither will return the file contents itself.
