<p align="center">
<img src = "https://user-images.githubusercontent.com/115906305/196015137-dcd5b06d-d24c-4db4-b125-c50592d5fd31.png" width = "300">
</p>

# Hey, this is UCT's Github!  

> **Note**:
> UCT's source code is not open source (yet!). So, ignore the README below until it becomes open source (or if you are the next generation of developers). 

Here you will be able to find other components or repos that may be helpful to beginners looking to get into participating in UCT or to other organisation wanting to start similar competitions. 

UCT's website can be found at [theuct.ca](https://www.theuct.ca).

Follow our organisation on Github here or on Instagram/Twitter at **theuctorg**. 

For any concerns or inquiries, please contact us through [our contact form](https://www.theuct.ca/contact) or shoot us an email at [contact@theuct.ca](mailto:contact@theuct.ca).

# United Coding Tournament

The United Coding Tournament (UCT) is a competition in a final-answer elimination-based tournament format. It features three rounds each with three questions. Each round lasts one hour. Participants are scored based on correctness and speed.

# Installation

* VS Code
    * Navigate to the [Visual Studio Code setup guide](https://code.visualstudio.com/docs/setup/setup-overview) to set up Visual Studio Code
* Postgres 14
    * Navigate to the [Postgres 14 download page](https://www.postgresql.org/download/)
    * Download version 14.8
    * During the installation, make sure of the following:
        * pgAdmin 4 is in the selected components to install
        * Host is **localhost**
        * User Name is **postgres**
        * Port is **Port 5432**
        * Note down the passwords used for superuser and postgres
* Go (lang)
    * Navigate to the [intallation guide](https://go.dev/doc/install) to set up Go
 
## Running the Code Locally

1. Create a folder named "uct". Move the extracted goweb folder into this folder
2. Open PgAdmin4. Enter the master password (superuser password)
3. Click on "Servers". Enter the password for the user postgres
4. Click on "Databases". If a database titled "uct" is not created, right click "Databases" and create a database with the name "uct" and owner "postgres"
5. In the uct database, navigate to Schemas
6. Click the dropdown on Schemas and navigate to Tables
7. Right-click tables and create a table as following:
    * In the General tab, set the name of the table as "problems_lists"
    * In the Columns tab, create a table with 9 columns with names as following
        * name
        * difficulty
        * tags
        * description
        * answer
        * input
        * solution
        * correct_users
        * wrong_users
    * Tick off "Primary key?" for the name column
    * All columns have the data type "text"
8. Open Visual Studio Code and open the goweb folder
9. Create a file named `password.env`
    * On the first line, write `DATABASEPASSWORD=" "` where your password for the postgres user goes in the quotations
    * On the second line, write `EMAILPASSWORD = "rwmabzmznaenzefy"`
9. Open the powershell terminal and make sure you are in the goweb directory. You may change directories by using the command `cd`
10. Type `go run .` in the terminal. If it shows that go is not installed, make sure that go is set to the appropriate PATH
11. Open a browser and go to http://localhost/
12. Create an account
13. In pgAdmin4, click on the uct database and then open the query tool
14. In the query tool, run `select * from public.Users`
15. For your account, go to the "active" column and change the value to 1 and save the data change
16. You can now use the UCT website locally without any issues

## Getting Admin Access

To get admin access, add the email for the account you wish to have access permissions into the slice, **AdminEmails** in the **AdminAuth** function located in admin.go

# Known Bugs/Errors
Unfortunately many issues are undocumented. Below are issues that have been documented:

## Security
* Remove sslcrt.key, sslcrt.pem, and log.txt files from the GitHub before making this project open source 
* Project was programmed assuming the source code is private; please carefully ensure there are no security/privacy risks before publicizing it (or don't make it open source)

## Problem Set
* Several problems found in the problems repository/past contest archives are either unfinished or incorrect

## Leaderboard
* Scores sometimes display as very bizarre numbers

## Archive Page
* Archive link currently does not redirect to the proper archive page
* Lack of good LaTeX formatting for displaying problem statements
* File input for uploading new problems does not include error checking for correct file type
* Lack of checking of the content of uploaded files for new problems
* Text input parameters for uploading new problems do not include error checking for specific style guidelines
* No cues on interface if filters are currently active in the archive page apart from the URL
* If admin is filling out the form to add the problem and admin closes the form and filters the problem list, the form will be cleared
* There is no error checking for inserting duplicate problems
    * Database will throw an error, although code does keep running
* Errors relating to database actions are logged but the code does not stop running
