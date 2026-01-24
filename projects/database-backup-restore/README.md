# Database Backup, Restore & Import/Export

## Overview
This project demonstrates performing backups, restores, imports and exports across MySQL and MongoDB. It covers full database backups, selective table exports, restoring to new databases, importing JSON data, and exporting collections to CSV. The goal is to practice data protection and recovery techniques and become familiar with CLI tools for relational and NoSQL databases.

## What I Did
- In MySQL:
  - Took a full backup of the existing database using `mysqldump` and saved it to a SQL dump file【226574213279189†L17-L24】.
  - Created a new database (`assignment5`) and restored the SQL dump into it【226574213279189†L17-L24】.
  - Exported just the `item` table from the `sampleData` database【226574213279189†L24-L25】.
- In MongoDB:
  - Used `mongodump` to back up the `test1` database to a backup directory【226574213279189†L33-L51】.
  - Restored the backup back into the `test1` database and also into a new `assignment5` database while keeping the original intact【226574213279189†L61-L66】.
  - Imported a JSON file (`stocks.json`) into the `sampleData` database using `mongoimport` after transferring it to the server with FileZilla【226574213279189†L68-L91】.
  - Exported the `occupation` collection from `sampleData` to a CSV file using `mongoexport` with selected fields【226574213279189†L94-L111】.

## Sample Commands
```bash
# MySQL: backup entire database
mysqldump -u user -p sampleData > sampleData.sql

# Restore to a new database
mysql -u user -p -e "CREATE DATABASE assignment5;"
mysql -u user -p assignment5 < sampleData.sql

# Export only the 'item' table
mysqldump -u user -p sampleData item > item.sql
``# Database Backup, Restore & Import/Export

## Overview
This project demonstrates performing backups, restores, imports and exports across MySQL and MongoDB. It covers full database backups, selective table exports, restoring to new databases, importing JSON data, and exporting collections to CSV. The goal is to practice data protection and recovery techniques and become familiar with CLI tools for relational and NoSQL databases.

## What I Did
- In MySQL:
  - Took a full backup of the existing database using `mysqldump` and saved it to a SQL dump file【226574213279189†L17-L24】.
  - Created a new database (`assignment5`) and restored the SQL dump into it【226574213279189†L17-L24】.
  - Exported just the `item` table from the `sampleData` database【226574213279189†L24-L25】.
- In MongoDB:
  - Used `mongodump` to back up the `test1` database to a backup directory【226574213279189†L33-L51】.
  - Restored the backup back into the `test1` database and also into a new `assignment5` database while keeping the original intact【226574213279189†L61-L66】.
  - Imported a JSON file (`stocks.json`) into the `sampleData` database using `mongoimport` after transferring it to the server with FileZilla【226574213279189†L68-L91】.
  - Exported the `occupation` collection from `sampleData` to a CSV file using `mongoexport` with selected fields【226574213279189†L94-L111】.

## Sample Commands
```bash
# MySQL: backup entire database
mysqldump -u user -p sampleData > sampleData.sql

# Restore to a new database
mysql -u user -p -e "CREATE DATABASE assignment5;"
mysql -u user -p assignment5 < sampleData.sql

# Export only the 'item' table
mysqldump -u user -p sampleData item > item.sql
```

```bash
# MongoDB: backup a database
mongodump -d test1 -o /home/ubuntu/backup

# Restore into the same database
mongorestore -d test1 /home/ubuntu/backup/test1

# Restore into a new database
mongorestore -d assignment5 /home/ubuntu/backup/test1/

# Import a JSON file into sampleData
mongoimport -d sampleData --file /home/ubuntu/stocks.json

# Export a collection to CSV
mongoexport --db sampleData --collection occupation --type=csv --fields _id,occupation --out occupation.csv
```

## Lessons Learned
- Regular backups are essential for disaster recovery and should be stored securely off-site.
- Restoring backups to a new database allows testing of recovery procedures without overwriting production data【226574213279189†L17-L24】.
- Selective exports (tables or collections) can be used to migrate specific data sets or troubleshoot issues.
- Tools like FileZilla facilitate transferring large data files to and from servers prior to import/export.
- MongoDB’s `mongodump`/`mongorestore` and `mongoimport`/`mongoexport` utilities provide flexible options for JSON and CSV formats.

## Next Steps
- Automate scheduled backups using cron jobs or database-specific tools.
- Explore incremental and differential backups for MySQL and MongoDB.
- Integrate backup verification and monitoring to ensure restores complete successfully.
`

```bash
# MongoDB: backup a database
mongodump -d test1 -o /home/ubuntu/backup

# Restore into the same database
mongorestore -d test1 /home/ubuntu/backup/test1

# Restore into a new database
mongorestore -d assignment5 /home/ubuntu/backup/test1/

# Import a JSON file into sampleData
mongoimport -d sampleData --file /home/ubuntu/stocks.json

# Export a collection to CSV
mongoexport --db sampleData --collection occupation --type=csv --fields _id,occupation --out occupation.csv
```

## Lessons Learned
- Regular backups are essential for disaster recovery and should be stored securely off-site.
- Restoring backups to a new database allows testing of recovery procedures without overwriting production data【226574213279189†L17-L24】.
- Selective exports (tables or collections) can be used to migrate specific data sets or troubleshoot issues.
- Tools like FileZilla facilitate transferring large data files to and from servers prior to import/export.
- MongoDB’s `mongodump`/`mongorestore` and `mongoimport`/`mongoexport` utilities provide flexible options for JSON and CSV formats.

## Next Steps
- Automate scheduled backups using cron jobs or database-specific tools.
- Explore incremental and differential backups for MySQL and MongoDB.
- Integrate backup verification and monitoring to ensure restores complete successfully.
