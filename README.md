![udacity logo](https://s3-us-west-1.amazonaws.com/udacity-content/rebrand/svg/logo.min.svg "Udacity")
# Logs Analysis Tool - Udacity
### Full Stack Web Development ND
[Udacity.com](https://www.udacity.com)


_____________________

# About
This is a report applaction using python3, it connected to the news database , to analyas and 
give a report about changes in logs, views, and articles recoreds, it's connected to the news database 

   Prerequisites
* Python: 3.8 https://www.python.org/downloads/release/python-380/  
* Vagrant: https://releases.hashicorp.com/vagrant/  
* VirtualBox: 3 
* Git : https://git-scm.com/downloads 


## How To set up instal and see VM on windows:

# Database Tables :

## 1- authors
id | Bio | name
--- | --- | ---
*primary key* | `text` | **text**
1 | 2 | 3

## 2- articles
author | title | slug | lead  | body | time | id  
--- | --- | --- | --- | --- | --- | --- 
*foreign key* | **text** | **UNIQUE CONSTRAINT** | **Text** | **Primary key**
1 | 2 | 3 | 4 | 5 | 6 | 7

## 2- articles
Path | IP | Method | Status | Time | ID
--- | --- | --- | --- | --- | --- 
 **text** | **inet** | **text** | **text** | **timeStamp & TZ** | **integer (Primary)**
1 | 2 | 3 | 4 | 5 | 6
