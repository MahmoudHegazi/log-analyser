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


## How To set up VM and use this app on windows:

We're using tools called Vagrant and VirtualBox to install and manage the VM. 
You'll need to install these to do some of the exercises. 
The instructions on this page will help you do this.

[Download This File](https://github.com/udacity/fullstack-nanodegree-vm)

1. Download virtualBox, vagrant, GitBash
2. install them 
3. access vagrant file that You have downloadead
4. type vagrant up [Enter] 'It Will take long time'
5. type vagrant ssh

## how to access vagrant file:
1.  unzip The file u have downloaded and put it in Downloads folder.
2.  open GitBash and type cd Downloads [Enter]
3.  then ls and copy the file name Then click paste or control [shift] + [insert]
4.  use cd on the file name fullstack-nanodegree-vm
5.  then cd vagrant , and run vagrant up and vagrant ssh


# Database Tables :

## 1- authors  
#### Primary Key : id

id | Bio | name
--- | --- | ---
*integer* | `text` | **text**



## 2- articles 
#### Primary Key : id, UNIQUE CONSTRAINT : slug, foreign Key: author
 
author | title | slug | lead  | body | time | id  
--- | --- | --- | --- | --- | --- | --- 
**integer* | **text** | **text** | **Text** | **integer**


## 2- articles
#### Primary Key : id

Path | IP | Method | Status | Time | ID
--- | --- | --- | --- | --- | --- 
 **text** | **inet** | **text** | **text** | **timeStamp** | **integer**
 
 
 views:
 
```python
select articles.title, count(*) as a_views
from articles join log on log.path = concat('/article/', articles.slug)
group by articles.title order by a_views desc limit 3;
```


