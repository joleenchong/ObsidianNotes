A platform for collecting data & analysing resources.

![[Pasted image 20230708173918.png]]
Left: list of sources of logging & metric data to collect
Center: logging & metric data stored in central repos
Right: data is being used

Azure Log Analytics:
- tool for writing & running log queries on data gathered by Azure Monitor
- supports simple & complex queries & data analysis

Monitor Alerts:
- automated alerts when Monitor detects crossed threshold
- can also attempt corrective action on alert
- uses action groups to config who to notify and action to take

Application Insights:
- monitors web apps thru installed SDK or agent (supported in C#.NET, VB.NET, Java, JavaScript, Node.js, Python)
- can monitor:
	- request rates, response times, failure rates
	- dependency rates, response times, failure rates -> show whether external services slowing down performance
	- page views & load performances from users' browsers
	- AJAX calls from web pages
	- user & session counts
	- performance counters from Windows / Linux server machines

