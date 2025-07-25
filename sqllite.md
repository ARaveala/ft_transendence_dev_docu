SQLite uses database level locking, meaning only one write operation can happen at a time. If multiple parts of your app try to write simultaneously, things can slow down or even fail.
Everything is stored in one file. That’s great for portability, but it can become a bottleneck for large scale apps or when you need distributed access.
performance tends to degrade once you hit a few gb especially without careful indexing and query optimization
No stored procedures, limited trigger support, and no full outer joins. If your app or framework expects these features, you’ll need workarounds
SQLite doesn’t offer robust user management or access control like PostgreSQL or MySQL. If your app needs fine-grained permissions, you’ll have to implement them manually
SQLite uses “manifest typing,” which means it doesn’t strictly enforce column types. This can lead to unexpected behavior if your app assumes strict typing
Easy to set up no server required
Often used in mobile apps and browser extensions
check how compatible SQLlite is against modules
