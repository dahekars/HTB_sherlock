
![images/jingle bell.png](https://github.com/dahekars/HTB_sherlock/blob/main/Jingle_Bell/images/jingle%20bell.png)
# Jingli bell

## Story
Torrin is suspected to be an insider threat in Forela. He is believed to have leaked some data and removed certain applications from their workstation. They managed to bypass some controls and installed unauthorized software. Despite the forensic team's efforts, no evidence of data leakage was found. As a senior incident responder, you have been tasked with investigating the incident to determine the conversation between the two parties involved.
## Technologies
1. Windows
2. Sqlite
3. Db browser for SQLite
4. Python3

## Task
1. Open the zip 
2. open path C/Users/AppData/Local/Microsoft/Windows/Notifications from the zip file 
3. Open wpndatabase.db file in the Db browser for SQLite
4. Click *browse data* tab
5. Select *Notification* table 
6. Set *Type* filter to **toast**

## Questions 
1. What's the channel name in which they conversed with each other?

Ans. Slack

Analysis: when checking the database entry, the user is using Slack application for data licking 

![Jingle_Bell/images/Pasted image 20240427150007.png](https://github.com/dahekars/HTB_sherlock/blob/main/Jingle_Bell/images/Pasted%20image%2020240427150007.png)

2. What's the name of the rival company to which Torrin leaked the data?

Ans. PrimeTech Innovations

Analysis. In the header section of the database entry the title contains the name of the company

3. What is the username of the person from the competitor organization whom Torrin shared information with?

Ans. Cyberjunkie-PrimeTechDev

Analysis. In one of the entries, the user got the notification for an accepted invite from Slack

4. What's the channel name in which they conversed with each other?

Ans. forela-secrets-leak

Analysis. After the invite was accepted all the conversation notifications came from the channel name "forela-secrets-leak"

5. What was the password for the archive server?

Ans. Tobdaf8Qip$re@1

Analysis. In one entry of notification, the user got a password notification for a password for sharing files

6. What was the URL provided to Torrin to upload stolen data to?

Ans. https://drive.google.com/drive/folders/1vW97VBmxDZUIEuEUG64g5DLZvFP-Pdll?usp=sharing

Analysis. In one conversation Cyberjunkie-PrimeTechDev shared a Google Drive link for uploading data

7. When was the above link shared with Torrin?

Ans. 2023-04-20 10:34:49

Analysis. there is the message time stamp in the epoch string which can be converted with python3 using the below code 

```python3
import datetime
epoch_time = 1681986889.660179
timestamp = datetime.datetime.fromtimestamp(epoch_time)
print(timestamp)
```
8. For how much money did Torrin leak Forela's secrets?

Ans. £10000

Analysis. In the last entry for Slack notification, the Cyberjunkie-PrimeTechDev sent £10000 to bank account 03135905179789

## Summary 
This incident happened in PrimeTech Innovations where the suspect (Torrin) is considered to be sharing Forela oil data with Cyberjunkie-PrimeTechDev over Slack application/ software. We have got a Wpndatabase.db database from the system. I have analyzed Wpndatabase.db file for all system notifications and found the conversation between the suspect and Cyberjunkie-PrimeTechDev.
The threat actor has shared the data over Google Drive for the amount of £10000 in account 03135905179789. 
