### Search for a Single Fluxx Record

This action allows you retrieve a Fluxx record via arbitrary SQL-like search. If you already have a record id, you should use the "Fetch Record by Id" Action instead of this one. This Action is better suited to more complex retrievals where you do not have the id of the record, but have to search with a more complex filter.

As the search may return more than one item, only the _first_ item returned will be used by Zapier, so you may wish to use an `ORDER BY` clause, and `LIMIT 1` in order to place the most relevant item at the start of the list. e.g.

* to use the most recent match: `ORDER BY updated_at desc LIMIT 1`
* to use the largest grant request: `ORDER BY amount_requested desc LIMIT 1`

* **Input**
  * **SQL input**: see [_SQL Support_](../Special/SQL_Support.md) e.g. `SELECT id, account_name, account_number FROM BankAccount WHERE owner_organization_id = [[ id from previous step ]] AND active = 1 ORDER BY updated_at desc LIMIT 1`
  * **Show MAVs**: indicate True/False (default False). If true, any Model Attribute Values returned will return percentage value (if available) and hierarchy information as described above.

* **Output**
```
id: 17443
model_type: bank_account
fields:
  id: 17443
  account_name: Save The Kids Trust
  account_number: 12-3456-1234567-000
  (all other requested fields appear here)
```