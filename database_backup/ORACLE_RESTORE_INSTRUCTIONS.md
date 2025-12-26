# Oracle Database Restore Instructions

This guide provides instructions for restoring the Oracle database backup located in the `database backup` directory.

**Note:** These instructions assume the backup is a Data Pump Export file (`.dmp`). If you have a legacy export or RMAN backup, steps will differ.

---

## Prerequisites

1.  **Backup File:** Ensure you have the `.dmp` file (e.g., `attendance.dmp`) available in your `database backup` folder.
2.  **Oracle Database:** You must have an Oracle instance running (either locally or in a Docker container).
3.  **Credentials:** You need `SYSDBA` access or a user with the `DATAPUMP_IMP_FULL_DATABASE` role.

---

## Scenario 1: Restore to Docker Container

### Step 1: Copy Backup to Container

First, copy the backup file from your host machine into the Docker container.

```bash
# Syntax: docker cp <local_path_to_dmp> <container_name>:<container_path>
# Example assuming your container is named 'oracle-db'
docker cp "../database backup/attendance.dmp" oracle-db:/opt/oracle/oradata/attendance.dmp
```

### Step 2: Access the Container

Log in to the container's shell and ensure file permissions are correct.

```bash
docker exec -it oracle-db /bin/bash

# Change ownership to oracle user (if necessary)
chown oracle:oinstall /opt/oracle/oradata/attendance.dmp
```

### Step 3: Create Oracle Directory Object

Log in to SQL*Plus as SYSDBA to define where the file is located inside the container.

```bash
sqlplus / as sysdba
```

Run the following SQL commands:

```sql
-- Create a directory object pointing to the location where you copied the file
CREATE OR REPLACE DIRECTORY dump_dir AS '/opt/oracle/oradata/';

-- Grant permissions to the user who will perform the import (e.g., SYSTEM)
GRANT READ, WRITE ON DIRECTORY dump_dir TO SYSTEM;

-- Exit SQL*Plus
EXIT;
```

### Step 4: Run Data Pump Import (impdp)

Execute the import command from the container shell.

```bash
impdp SYSTEM/password@//localhost:1521/ORCLCDB DIRECTORY=dump_dir DUMPFILE=attendance.dmp LOGFILE=restore.log FULL=Y
```

*Note: Replace `ORCLCDB` with your specific Service Name (e.g., `ORCLPDB1` for pluggable databases).*

---

## Scenario 2: Restore to Local Machine

### Step 1: Prepare the Directory

Identify the absolute path to your backup folder.
Example Path: `/Users/bharathiguntikovila/Documents/attendance/database backup/`

### Step 2: Create Oracle Directory Object

Open your terminal and log in to SQL*Plus.

```bash
sqlplus / as sysdba
```

Run the following SQL commands:

```sql
-- Point this path to your actual local backup folder
CREATE OR REPLACE DIRECTORY local_dump_dir AS '/Users/bharathiguntikovila/Documents/attendance/database backup/';

-- Grant permissions
GRANT READ, WRITE ON DIRECTORY local_dump_dir TO SYSTEM;

EXIT;
```

### Step 3: Run Data Pump Import

Run the import command from your terminal.

```bash
impdp SYSTEM/password@//localhost:1521/ORCL DIRECTORY=local_dump_dir DUMPFILE=attendance.dmp LOGFILE=restore_local.log FULL=Y
```

---

## Common Troubleshooting

*   **ORA-39002: invalid operation**: Check that the directory path exists and the Oracle OS user has read/write permissions on that folder.
*   **ORA-39083: Object type ... failed to create**: If the user/tables already exist, add `TABLE_EXISTS_ACTION=REPLACE` to your `impdp` command.
*   **Tablespace errors**: If the source database used different tablespace names, use `REMAP_TABLESPACE=source_ts:target_ts`.
