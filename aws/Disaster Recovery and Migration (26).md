- RPO & RTO
	- Recovery Point Objective: what point you reset from. Data lost btw that point and disaster.
	- Recovery Time Objective: how much downtime is ok after disaster
- Disaster Recovery Strategies (4 types) ^9269e3
	- Backup & Restore
	- Pilot Light: small version (central core) of app always running as backup. Similar to but faster than B&R since core systems are already up. E.g. db kept running so backups can be sent immediately, EC2 needs restarted. 
	- Warm Standby: full system up & running at min. size, can quickly scale to production load.
	- Multi-/ Hot Site: second full production scale system always up and running. 
- Tools: DMS and SMS
	- database migration service: fast/ secure db migration to AWS. Continuous data replication using CDC (change data catcher). Source db remains avail during migration. 
		- to use: create EC2 instance to perform replications tasks (i.e. running DMS). if source and dest db do not have same engine: AWS SCT (schema migration tool)
	- Server Migration Service: incremental replication of on-prem live servers to AWS
- AWS Data Sync
	- replicate data from on-prem to AWS digitally, to S3, EFS, FSx. Can schedule hourly, daily, weekly. To use, install DataSync agent on-prem.
	- move from your NAS (network attached storage) or file system via NFS, SMB
- AWS Backup
	- fully managed service to centrally manage/automate backups across AWS services. Cross-region and cross-account. 
	- Set backup policies ("backup plans"): tag based, set frequency, window, if/when to transition to cold storage, retention pd.