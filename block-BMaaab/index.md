writeCode

Run these shell commands in mongo shell:

- db.version()
  > 6.0.0
- db.stats()

```json
{
  "db": "test",
  "collections": 0,
  "views": 0,
  "objects": 0,
  "avgObjSize": 0,
  "dataSize": 0,
  "storageSize": 0,
  "indexes": 0,
  "indexSize": 0,
  "totalSize": 0,
  "scaleFactor": 1,
  "fsUsedSize": 0,
  "fsTotalSize": 0,
  "ok": 1
}
```

- db.help()
  - db.getMongo = Returns the current database connection
  - db.getMongo = Returns the current database connection
  - db.getName = Returns the name of the DB
  - db.getCollectionNames = Returns an array containing the names of all collections in the current database.
  - db.getCollectionInfos = Returns an array of documents with collection information, i.e. collection name and options, for the current database.
  - db.runCommand = Runs an arbitrary command on the database.
  - db.adminCommand = Runs an arbitrary command against the admin database.
  - db.aggregate = Runs a specified admin/diagnostic pipeline which does not require an underlying collection.
  - db.getSiblingDB = Returns another database without modifying the db variable in the shell environment.
  - db.getCollection = Returns a collection or a view object that is functionally equivalent to using the db.<collectionName>.
  - db.dropDatabase = Removes the current database, deleting the associated data files.
  - db.createUser = Creates a new user for the database on which the method is run. db.createUser() returns a duplicate user error if the user already exists on the database.
  - db.updateUser = Updates the user’s profile on the database on which you run the method. An update to a field completely replaces the previous field’s values. This includes updates to the user’s roles array.
  - db.changeUserPassword = Updates a user’s password. Run the method in the database where the user is defined, i.e. the database you created the user.
  - db.logout = Ends the current authentication session. This function has no effect if the current session is not authenticated.
  - db.dropUser = Removes the user from the current database.
  - db.dropAllUsers = Removes all users from the current database.
  - db.auth = Allows a user to authenticate to the database from within the shell.
  - db.grantRolesToUser = Grants additional roles to a user.
  - db.revokeRolesFromUser = Removes a one or more roles from a user on the current database.
  - db.getUser = Returns user information for a specified user. Run this method on the user’s database. The user must exist on the database on which the method runs.
  - db.getUsers = Returns information for all the users in the database.
  - db.createCollection = Create new collection
  - db.createView = Create new view
  - db.createRole = Creates a new role.
  - db.updateRole = Updates the role’s profile on the database on which you run the method. An update to a field completely replaces the previous field’s values.
  - db.dropRole = Removes the role from the current database.
  - db.dropAllRoles = Removes all roles from the current database.
  - db.grantRolesToRole = Grants additional roles to a role.
  - db.revokeRolesFromRole = Removes a one or more roles from a role on the current database.
  - db.grantPrivilegesToRole = Grants additional privileges to a role.
  - db.revokePrivilegesFromRole = Removes a one or more privileges from a role on the current database.
  - db.getRole = Returns role information for a specified role. Run this method on the role’s database. The role must exist on the database on which the method runs.
  - db.getRoles = Returns information for all the roles in the database.
  - db.currentOp = Calls the currentOp command. Returns a document that contains information on in-progress operations for the database instance. The db.currentOp() method wraps the database command currentOp.
  - db.killOp = Calls the killOp command. Terminates an operation as specified by the operation ID. To find operations and their corresponding IDs, see $currentOp or db.currentOp().
  - db.shutdownServer = Calls the shutdown command. Shuts down the current mongod or mongos process cleanly and safely. You must issue the db.shutdownServer() operation against the admin database.
  - db.fsyncLock = Calls the fsync command. Forces the mongod to flush all pending write operations to disk and locks the entire mongod instance to prevent additional writes until the user releases the lock with a corresponding db.fsyncUnlock() command.
  - db.fsyncUnlock = Calls the fsyncUnlock command. Reduces the lock taken by db.fsyncLock() on a mongod instance by 1.
  - db.version = returns the db version. uses the buildinfo command
  - db.serverBits = returns the db serverBits. uses the buildInfo command
  - db.isMaster = Calls the isMaster command
  - db.hello = Calls the hello command
  - db.serverBuildInfo = returns the db serverBuildInfo. uses the buildInfo command
  - db.serverStatus = returns the server stats. uses the serverStatus command
  - db.stats = returns the db stats. uses the dbStats command
  - db.hostInfo = Calls the hostInfo command
  - db.serverCmdLineOpts = returns the db serverCmdLineOpts. uses the getCmdLineOpts command
  - db.rotateCertificates = Calls the rotateCertificates command
  - db.printCollectionStats = Prints the collection.stats for each collection in the db.
  - db.getFreeMonitoringStatus = Calls the getFreeMonitoringStatus command
  - db.disableFreeMonitoring = returns the db disableFreeMonitoring. uses the setFreeMonitoring command
  - db.enableFreeMonitoring = returns the db enableFreeMonitoring. uses the setFreeMonitoring command
  - db.getProfilingStatus = returns the db getProfilingStatus. uses the profile command
  - db.setProfilingLevel = returns the db setProfilingLevel. uses the profile command
  - db.setLogLevel = returns the db setLogLevel. uses the setParameter command
  - db.getLogComponents = returns the db getLogComponents. uses the getParameter command
  - db.cloneDatabase = deprecated, non-functional
  - db.cloneCollection = deprecated, non-functional
  - db.copyDatabase = deprecated, non-functional
  - db.commandHelp = returns the db commandHelp. uses the passed in command with help: true
  - db.listCommands = Calls the listCommands command
  - db.getLastErrorObj = Calls the getLastError command
  - db.getLastError = Calls the getLastError command
  - db.printShardingStatus = Calls sh.status(verbose)
  - db.printSecondaryReplicationInfo = Prints secondary replicaset information
  - db.getReplicationInfo = Returns replication information
  - db.printReplicationInfo = Formats sh.getReplicationInfo
  - db.printSlaveReplicationInfo = DEPRECATED. Use db.printSecondaryReplicationInfo
  - db.setSecondaryOk = This method is deprecated. Use db.getMongo().setReadPref() instead
  - db.watch = Opens a change stream cursor on the database
  - db.sql = Experimental) Runs a SQL query against Atlas Data Lake. Note: this is an experimental feature that may be subject to change in future releases.

Write code to

- create a database of your country name.
  > use india
- check list of databases to see newly created database.
  > show dbs
  >
  > - admin 40.00 KiB
  > - config 108.00 KiB
  > - local 40.00 KiB
- check which database you are currently connected to ?
  > db.getName()
  >
  > - india
