---
layout: post
title: Observability and Monitoring
---

# Observability  
- Measuring internal state of a system from knowledge of external output 

## Key tenants of Observability 
- Logging  
- Tracing  
- Monitoring  
- Alerting  

## Logging  
- Log Levels  
- Structured Logging  
  - have a fixed strucutre for all the logs  
  - Segregate the diff info into diff fileds such as status, message, data etc...  
- Log Aggregrators  
  - All the logs related to a flow should be bundled together, using a session kind of functionality k/as **correlation id**  
  - It should not be scattered otherwise it will be difficult to track issues since logs from different flows, diff users will be there and difficult to isolated the logs related to the flow  
- Log Visualization  
- Disk Space  

