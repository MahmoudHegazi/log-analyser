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

## DataBase Download:
[DownLoad](https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip)
You will need to unzip this file after downloading it. The file inside is called newsdata.sql. 
Put this file into the vagrant directory, which is shared with your virtual machine.

!To build the reporting tool, you'll need to load the site's data into your local database.

cd into the vagrant directory and use the command psql -d news -f newsdata.sql

*. psql — the PostgreSQL command line program
*. -d news — connect to the database named news which has been set up for you
*. -f newsdata.sql — run the SQL statements in the file newsdata.sql

## Getting an error?

If this command gives an error message, such as 
psql: FATAL: database "news" does not exist
psql: could not connect to server: Connection refused
this means the database server is not running or is not set up correctly Download:

[Download](https://www.google.com " download the virtual machine configuration")

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


## 3- Log
#### Primary Key : id

Path | IP | Method | Status | Time | ID
--- | --- | --- | --- | --- | --- 
 **text** | **inet** | **text** | **text** | **timeStamp** | **integer**
 
 
 views:
### Return What are the most popular three articles of all time?
```python
select articles.title, count(*) as a_views
from articles join log on log.path = concat('/article/', articles.slug)
group by articles.title order by a_views desc limit 3;
```

### Return Who are the most popular article authors of all time?
```python
   SELECT authors.name, COUNT(*) AS views
            FROM authors JOIN articles
             ON authors.id = articles.author
            JOIN log
             ON log.path = concat('/article/', articles.slug)
            GROUP BY authors.name
            ORDER BY views DESC
```

### On which days did more than 1% of requests lead to errors?
```python
   create view days_errors as                                                 
   select cast(time as date) as dte, count(*) as errors
   from log  where status != '200 OK' 
   group by cast(time as date)
   order by errors desc;
```
```pthon
select dte, errors from days_errors group by dte,
errors having errors > sum(errors) / 100 order by errors desc;
```


### return in which day there was the max errors
```python
   select dte, errors from days_errors 
   group by dte, errors having errors > sum(errors) / 100 
   order by errors desc limit 1;
```   


   
## Author:
   ### Mahmoud Hegazy   
   ![author photo](https://avatars2.githubusercontent.com/u/55125302?s=96&v=4 "Author")
