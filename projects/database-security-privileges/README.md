# Database Security & User Privileges

## Overview
This project demonstrates creating and managing user accounts and privileges across MySQL and MongoDB. The goal is to practice principle-of-least-privilege, grant/revoke rights using SQL and NoSQL commands, and compare the level of detail offered by command-line tools versus GUI.

## What I Did
- Created a new MySQL user (initial+lastname) that can only connect from the local host.
- Granted this user full privileges on the acme database with the ability to grant those privileges to others.
- Granted the user read-only access to the `country` table in the `sampleData` database without the grant option.
- Created a MongoDB user in the `sampleData` database with read-only role using `mongosh`.
- Explored the "Users and Privileges" tab in MySQL Workbench and noted differences from CLI.

## Sample Commands
```sql
-- MySQL: create a local user
CREATE USER 'username'@'localhost' IDENTIFIED BY 'YourStrongPassword';
FLUSH PRIVILEGES;

-- Grant all privileges with grant option
GRANT ALL ON acme.* TO 'username'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

-- Grant read-only on a single table
GRANT SELECT ON sampleData.country TO 'username'@'localhost';
FLUSH PRIVILEGES;
```

```javascript
// MongoDB: create user with read role in sampleData
db.createUser({
  user: "username",
  pwd: "YourStrongPassword",
  roles: [ { role: "read", db: "sampleData" } ]
});
```

## Lessons Learned
- The MySQL CLI provides more granular visibility and control than the MySQL Workbench GUI, which doesn't display authentication methods, role assignments or host restrictions【351862302534528†L74-L83】.
- Host-based access control and the grant option should be carefully set to enforce least privilege.
- MongoDB user roles follow a role-based access control model; using the appropriate role (e.g. `read`) limits access to what is necessary.

## Next Steps
- Explore revoking privileges and auditing user activity.
- Implement more fine-grained roles (e.g. `readWrite`) and test access.
- Compare additional GUI tools with CLI to understand their limitations.
