# Splunk Exploring SPL 

<h2>Description</h2>
<b>Splunk is a leading SIEM solution that enables real-time collection, analysis, and correlation of network and machine logs. In this module, we will explore the fundamentals of Splunk, its core functionalities, and how it enhances visibility into network activities while accelerating threat detection.

Splunk’s powerful capabilities allow users to search and analyze machine data efficiently. It uses Search Processing Language (SPL) to perform advanced searches. SPL includes a wide range of functions and commands that can be combined to create complex yet effective queries for optimized results.</b>

<h2>🎯 What You Will Learn</h2>
<ul>
  <li>How to navigate the Splunk Search & Reporting interface</li>
  <li>Basics of Splunk Search Processing Language (SPL)</li>
  <li>How to filter and analyze log data using SPL commands</li>
  <li>Use of SPL commands such as <code>table</code>, <code>chart</code>, <code>dedup</code>, <code>reverse</code>, <code>top</code>, and <code>rare</code></li>
  <li>How to interpret search results to identify hosts, IP addresses, event patterns, and user activity</li>
</ul>
<h2>Environments & Tools Used </h2>

- <b>TryHackMe</b>
- <b>Splunk</b>
- <b>Logs</b>

<h2>Here, I will focus on Index Windowslogs</h2>

<b> Let's open splunk: </b>

<b> Click on "Search and Reporting" to begin, then answer the questions below: </b>
<img width="1894" height="813" alt="image" src="https://github.com/user-attachments/assets/b8cb38ba-cba7-4d2e-8aef-d0633718a985" />

<b>Q: What is the name of the host in the Data Summary tab?</b><br>
ADD index=windowslogs * is used to filter data from the “windowslogs” index, showing all events represented by the asterisk (). Time filter set to all, to get all the existing logs

<img width="1897" height="734" alt="image" src="https://github.com/user-attachments/assets/912327f7-69be-4901-97a7-29dc71bd61e8" />

<b>Answer: Cyber-host </b>

<b>Familiarize Yourself with the UI:</b>

Search & Reporting App is the default interface used to search and analyze the data on the Splunk Home page. It has various functionalities that assist analysts in improving the search experience.

<img width="1895" height="691" alt="image" src="https://github.com/user-attachments/assets/1bc6eefb-1cc4-4fa9-9ee4-235ffa7bf382" />

Some important functionalities present in the search App are explained below:

<b> 1) Search Head: </b>
   
Search Head is where we use search processing language queries to look for the data.

<img width="1165" height="201" alt="image" src="https://github.com/user-attachments/assets/f1889841-c1bb-4cde-ad32-fd1af931aef8" />

<b> 2) Time Duration: </b>
   
This tab option provides multiple options to select the time duration for the search. All-time will display the events in real-time. Similarly, the last 60 minutes will display all the events captured in the last hour.

<img width="1180" height="863" alt="image" src="https://github.com/user-attachments/assets/ae0f135a-580b-4a4d-ba76-d846305d06b6" />

<b> 3) Search History: </b>
   
This tab saves the search queries that the user has run in the past along with the time when it was run. It lets the user click on the past searches and look at the result. The filter option is used to search for the particular query based on the term.

<img width="1887" height="576" alt="image" src="https://github.com/user-attachments/assets/6b0d9b28-7560-4b78-8218-18e5613dd24b" />

<b> 4) Data Summary: </b>
   
This tab provides a summary of the data type, the data source, and the hosts that generated the events as shown below. This tab is very important feature used to get a brief idea about the network visibility.

<img width="879" height="553" alt="image" src="https://github.com/user-attachments/assets/ff9072ec-7ffb-43c9-9545-08c670645a79" />

<b> 5) Field Sidebar: </b>

The Field Sidebar can be found on the left panel of Splunk search. This sidebar has two sections showing selected fields and interesting fields. It also provides quick results, such as top values and raw values against each field.

<img width="1599" height="755" alt="image" src="https://github.com/user-attachments/assets/d77c2b9d-6d18-424e-b7a3-643bfd04237b" />


<b>Question: In the search History, what is the 7th search query in the list? (excluding your searches from today)</b>

Setting no time filter to get all possible logs with the time duration set to week to date.
ignore all the logs for today and the answer can be obtained at the 7th place from the first search that did not occur today.

<img width="1844" height="769" alt="image" src="https://github.com/user-attachments/assets/e4c8767f-c08a-4c19-8cfd-ff9090a59dac" />

<b>Answer: index=windowslogs | chart count(EventCode) by Image</b>

<b>Question: In the left field panel, which Source IP has recorded max events?</b>
Hint: Look for SourceIP

<img width="1881" height="460" alt="image" src="https://github.com/user-attachments/assets/0de7ab90-19c5-4748-bdbf-411231da755b" />

<img width="709" height="461" alt="image" src="https://github.com/user-attachments/assets/9a3758d3-055a-41c2-bd47-3acf4d440c51" />

<b>Answer: 172.90.12.11</b>

<b>Question: How many events are returned when we apply the time filter to display events on 04/15/2022 and Time from 08:05 AM to 08:06 AM?</b>

<img width="1902" height="500" alt="image" src="https://github.com/user-attachments/assets/a0ff5946-1afa-40ec-9d58-e61e103a8a44" />

<b>Answer: 134</b>

<b> Question: How many Events are returned when searching for Event ID 1 AND User as *James*? </b>

<img width="1899" height="458" alt="image" src="https://github.com/user-attachments/assets/6a2155c7-c169-4902-a966-f5be557e7aad" />

<b>Answer: 4 </b>

<b>Questions: How many events are observed with Destination IP 172.18.39.6 AND destination Port 135? </b>

index= windowslogs * DestinationIp="172.18.39.6" DestinationPort="135"
<img width="1893" height="786" alt="image" src="https://github.com/user-attachments/assets/be163ee9-05e1-485f-a985-a4e60d16af30" />

<b>Answer: 4 </b>

<b>Question: What is the Source IP with highest count returned with this Search query? </b>

Search Query: index=windowslogs  Hostname="Salena.Adam" DestinationIp="172.18.38.5"

<img width="1506" height="958" alt="image" src="https://github.com/user-attachments/assets/abcdcff3-e7f7-47c1-8aca-a0b46a46abdc" />

<b>Answer: 172.90.12.11 </b>
<b>Question: In the index windowslogs, search for all the events that contain the term cyber how many events returned? </b>

index=windowslogs* cyber 

<img width="1899" height="293" alt="image" src="https://github.com/user-attachments/assets/e839c224-8fa0-40c3-9e8c-8a2e532743df" />
<b> Answer: 0 </b>

<b>Question: Now search for the term cyber*, how many events are returned? </b>

<img width="1898" height="436" alt="image" src="https://github.com/user-attachments/assets/77e88b49-e9db-4cd2-90e3-6a3c42c82b8f" />

<b>Answer: 12256 </b>

<b>Question: What is the third EventID returned against this search query? </b>

Search Query: index=windowslogs | table _time EventID Hostname SourceName | reverse 

<img width="1881" height="941" alt="image" src="https://github.com/user-attachments/assets/78d76e9e-b6e1-4b0a-a78a-3360768455dc" />

<b>Answer: 4103</b>

<b>Question: Use the dedup command against the Hostname field before the reverse command in the query mentioned in Question 1. What is the first username returned in the Hostname field?</b>

<img width="1900" height="458" alt="image" src="https://github.com/user-attachments/assets/e43f1d23-639f-4d41-ba6e-6f8dcc484374" />

<b>Answer: Salena.Adam</b>

<b>Question: Using the Reverse command with the search query index=windowslogs | table _time EventID Hostname SourceName - what is the HostName that comes on top?</b>

<img width="1881" height="917" alt="image" src="https://github.com/user-attachments/assets/5339c323-fbc0-4ab3-a50c-46d9846c8cf2" />

<b>Answer: James.browne </b>

</b>Question: What is the last EventID returned when the query in question 1 is updated with the tail command?</b>

<img width="1887" height="673" alt="image" src="https://github.com/user-attachments/assets/cc4bb46c-6fd6-4840-80a4-271406b3c9b2" />

<b>Answer: 4103</b>

<b>Question: Sort the above query against the SourceName. What is the top SourceName returned?</b>

<img width="1889" height="406" alt="image" src="https://github.com/user-attachments/assets/20f0d315-0e55-461f-9fb8-34f4e2585e50" />

<b>Answer: Microsoft-Windows-Directory-Services-SAM</b>

<b>Question: List the top 8 Image processes using the top command -  what is the total count of the 6th Image?</b>

<img width="1900" height="598" alt="image" src="https://github.com/user-attachments/assets/08f40029-2484-401b-9efa-84b5b55a3063" />

<b>Answer: 196</b>

<b>Question: Using the rare command, identify the user with the least number of activities captured?<1b>

<img width="1894" height="619" alt="image" src="https://github.com/user-attachments/assets/e8f032ec-2108-4978-9335-d5eb5ef06cad" />

<b>Answer: James</b>

<b>Question: Create a pie-chart using the chart command - what is the count for the conhost.exe process?</b>

<img width="1898" height="693" alt="image" src="https://github.com/user-attachments/assets/4d4c1fa3-2e70-4f0d-81e2-32a746a7b198" />

<img width="1894" height="572" alt="image" src="https://github.com/user-attachments/assets/0c302a04-51d6-4542-b768-537ea900b00a" />

<b>Answer: 70 </b>

🔍 <b>Summary
In this walkthrough, I explored Splunk’s interface and demonstrated how to use Search Processing Language (SPL) to filter, transform, and visualize machine data. Key concepts covered include using table, chart, dedup, reverse, top, rare, and other SPL commands to gain insights from Windows log events. </b>

<h2>Thank You</h2>
