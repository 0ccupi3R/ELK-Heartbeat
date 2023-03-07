# ELK-Heartbeat
"ELKHeartbeat" is a monitoring tool that alerts team when any device stops sending events to Elasticsearch. It helps ensure the smooth operation of the environment and prevents data loss.


Event flow -> 
1. Script will detect the current status of ELK/ Index count 
- If it’s green or more than threshold value --> Ignore 
- If it’s RED/YELLOW or index count is less than the threshold value or Zero --> Alert 
2. The alert will contains the basic information 
- Index name
- Last event received time 
3. The HIVE case will be created with all details.
4. Based on the above alert, next step will be executed to validate the respective server where agent (Logstash/Filebeat) installed:
- Check the current state of Logstash/Filebeat
- Fetch the last 100 logs foe each services and update the HIVE Case accordingly.
- Restart the service automatically and again send the logs for each services
5. This will help us to achieve two main goals :
- Decrease the failure/error detection time 
- Track the incident for infrastructure /components downtime.
