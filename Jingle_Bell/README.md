
![images/jingle bell.png](https://github.com/dahekars/HTB_sherlock/blob/main/Jingle_Bell/images/jingle%20bell.png)
# Jingli bell

## Story
Torrin is suspected to be an insider threat in Forela. He is believed to have leaked some data and removed certain applications from their workstation. They managed to bypass some controls and installed unauthorised software. Despite the forensic team's efforts, no evidence of data leakage was found. As a senior incident responder, you have been tasked with investigating the incident to determine the conversation between the two parties involved.
## Technologies
1. Windows
2. Sqlite
3. Db browser for sqlite
4. Python3

## Task
1. Open the zip 
2. open path C/Users/Appdata/Local/Microsoft/Windows/Notifications from the zip file 
3. Open wpndatabase.db file in Db browser for sqlite
4. Click *browse data* tab
5. Select *Notification* table 
6. Set *Type* filter to **toast**
## Questions 
1. What's the channel name in which they conversed with each other?
ans. Slack
analysis: when checked the database entry, user is using Slack application for data licking 

![[Jingle_Bell/images/Pasted image 20240427150007.png]]

2. What's the name of the rival company to which Torrin leaked the data?
ans. PrimeTech Innovations
analysis. In header section of database entry the title contains the name of the company

. What is the username of the person from the competitor organization whom Torrin shared information with?
	ans. Cyberjunkie-PrimeTechDev
	analysis. in one of the entries the user got the notification for accepted invite from slack
5. What's the channel name in which they conversed with each other?
	ans. forela-secrets-leak
	analysis. After the invite was accepted all the conversation notification came from channel name "forela-secrets-leak"
6. What was the password for the archive server?
	ans. Tobdaf8Qip$re@1
	analysis. in one entry of notification user got password notification for password for sharing files
7. What was the URL provided to Torrin to upload stolen data to?
	ans. https://drive.google.com/drive/folders/1vW97VBmxDZUIEuEUG64g5DLZvFP-Pdll?usp=sharing
	analisys. in one conversation Cyberjunkie-PrimeTechDev shared a google drive link for uploading data
8. When was the above link shared with Torrin?
	ans. 2023-04-20 10:34:49
	analysis. there is the message time stamp in epoch string with can be converted with python3 using below code 
```python3
import datetime
epoch_time = 1681986889.660179
timestamp = datetime.datetime.fromtimestamp(epoch_time)
print(timestamp)
```
8. For how much money did Torrin leak Forela's secrets?
	ans. £10000
	analysis. in last entry for Slack notification the Cyberjunkie-PrimeTechDev have send £10000 to bank account 03135905179789

## Summary 
This incident was happened in PrimeTech Innovations where suspect (Torrin) has considered to be sharing Forela oil data to Cyberjunkie-PrimeTechDev over Slack application/ software. We have got a Wpndatabase.db database from system. I have analysed Wpndatabase.db file for all system notifications and found conversation between suspect and Cyberjunkie-PrimeTechDev.
thread actor have shared the data over Google drive for amount of £10000 in the account 03135905179789. 
