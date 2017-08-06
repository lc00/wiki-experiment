* Can also connect based on events (use for event handlers)
* Can declare schemas
* model is an instance of schema
* `.find({}, callback);`
* `.save({});`
* Mongoose can use `.where().equals().limit().select()`
* Use `find` and then `save`, not `update`- `update` bypasses schema.
* Graceful shutdowns by listening for events (`SIGINT`, `SIGTERM`)
