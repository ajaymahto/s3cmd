# The script s3util performs the following functions.
- Backup of a given directory path into specific s3 bucket.
- Restore of a backed up path onto local machine.
- Force Backup/Restore to/from remote s3 bucket and localpath.
- Set retention strategy in days for the backed up path.

# Prerequisites.
- IAM Role with minimum privilege of write access to the s3 bucket.
- AWS CLI setup.

# Commands:
- Backup a path into a remote s3bucket
  - ```s3util --backup --path <path> --s3bucket <s3bucket>``` 
- Backup a path into a remote s3bucket with custom retention days. [Default retention: 10 days.]
  - ```s3util --backup --path <path> --s3bucket <s3bucket> --retention-days <ret_days>```

- Restore a backed path from a particular date onto local fs.
  - ```s3util --restore --path <path> --s3bucket <s3bucket> --date <backupDate>```
  - ```s3util --restore --path <path> --s3bucket <s3bucket> --latest [For latest backup]```

- Force restore/backup.
  - Backup
    - ```s3util --backup --force --path <path> --remote-path <Absolute s3path of the backup path>```
  - Restore
    - ```s3util --backup --force --path <path> --remote-path <Absolute s3path of the backup path>```
    - # s3path must be complete s3 path3://test-bucket01/test-host/2019-05-10/tmp/current
