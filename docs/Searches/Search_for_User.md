### Search for User

> This action allows you retrieve a Fluxx user by their full name. It returns their user id.

<p align="center"><img alt="Search for User" src="../../img/search_for_user.png" width="448px"></p>

* **Input**
  * **Name**: Enter the full name of the user you want to search for. The name can be provided statically or may be the result of a previous trigger or action.

  * **Should this step be considered a "success" when nothing is found?**: Sometimes it matters if the requested record exists, and sometimes it doesn't. Choosing "No" causes all subsequent steps to be skipped when nothing is found.

* **Output**
```
id: 12341
full_name: Jane Doe
_zap_search_was_found_status: true
```