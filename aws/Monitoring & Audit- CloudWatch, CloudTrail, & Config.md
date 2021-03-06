- AWS CloudWatch
	- provides metrics for every service in AWS. 
		- "metric": variable to monitor, e.g. CPU Utilization
		- metrics belong to *namespaces* (groups)
		- *dimension*: an attribute of a metric, e.g. instance ID (up to 10 dimensions/ metric)
	- EC2 Detailed Monitoring
		- usually, EC2 metrics pulled every 5 mins, w/ detailed monitoring you get every 1 min.
	- Cloudwatch Custom Metrics- define and send your own metrics to cloudwatch.
		- metric resolution- standard = 1min, high (^$) = 1sec. Use exponential backoff in case of throttle errors.
	- Cloudwatch Dashboards: *global*, can incl. graphs from different regions
	- CloudWatch Logs
		- collect logs from: Elastic Beanstalk, ECS, Lambda, VPC Flow Logs, API GW, CloudTrail, R53, CloudWatch log agents
		- send logs to: stream to ElasticSearch cluster for more analysis, batch export to S3 for archival
		- to set up, specify log group (arbitrary name, usually reps application) and log stream (instances w/in app/log files/ containers)
		- security: IAM, KMS. expiration policy: never, 30 days, etc-- pay for retention
	- Cloudwatch Agent
			- push logs and metrics from EC2 into cloudwatch. 
			- 2 types: 
				- CW Logs Agent: old, only sends to CW logs
				- CW Unified Agent: new, collect additional system-level metrics. Centralized config using SSM Parameter Store
	- CloudWatch Alarms: trigger notifications for any metric
	- Cloudwatch events: can schedule cron jobs or set event pattern- rules to react to some event.
- AWS CloudTrail
	- governance, compliance, and audit for AWS accounts. Enabled by default. Log events'api calls made w/in your AWS account
		- trail can be applied to all regions (default) or a single region. Default retention is 90 days, can send to S3/ Cloudwatch logs
	- 3 kinds of events...
		- Management events- e.g. configuring security. Logged by default. 
		- Data events - e.g. s3 object-level activity
		- CloudTrail Insights Events - ETI is paid service to analyze acct activity and di=etect anything unusual. 
- AWS Config
	- helps w auditing and recording compliance of your AWS resources. record configurations and changes over time.
	- per-region service but can aggregate across regions and accounts
	- can use AWS managed config rules, or make custom config rules (defined in Lambda). Rules can have autoremediations. They do not prevent anything from happening. 
	- $2/rule/region/month
- CW v CT v Config	
	- CW: performance monitoring. Events and alerting. Log *aggregation* & analysis
	- CT: logging all API calls made w/in your acct, by everyone.
	- Config: record configuration changes and eval. responses against compliance rules.