### Trigger on New/Updated Records

* This is a traditional Zapier-style trigger, operating on a timed basis, and designed to detect new records added to Fluxx.
* It utilises Zapier's de-duping, so will not trigger more than once on the same record while the Zap is live. Be aware that the de-duping is reset if the Zap is stopped and re-started, so take care if you perform operations on a Fluxx record that should be only done once.
* Configuration of which records to return (i.e. which list of records will be regularly downloaded to check for additions) is done via FCE's [_SQL Support_](../Special/SQL_Support.md).
