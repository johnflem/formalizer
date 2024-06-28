# formalizer
Formalizer automated admin form creation
The Formalizer is a dynamic administrative tool for creating data entry and query forms for any sqlite database.

It runs as a uvicorn server, to be hosted on a nginx platform. Ideally this would be a subdomain of the main website, allowing only admins access to universal data entry.

Database requirements:
- All tables must have a primary autoincrement id named id
- Any table that is used as a parent table for a foreign key must have a column called name
- There must be a table named admins that will consist of a name, email, and password columns.

To run, 
- unzip the file into a candidate folder.
- create a sqlite database using the above criteria
- when complete, run “bash ./setup.sh {databasename}”
-   a virtual environment will be created
-  a pip install -r requirements.txt will populate external libraries
-  uvicorn app.main:app –reload will start.

Once the server is running,
- go to http://localhost:8000/admin
- you will be asked to log in (sample store.db has a root@root.com/password entry)
- once logged in, you will see a list of your tables in the left menu bar
- choose the table, you will see a form for that table.
- add rows by clicking on the new button
- choose the edit/delete buttons to change an existing record
- if a foreign key was identified and the above rules followed, there will be a dropdown for valid entry

Once you are satisfied, create a subdirectory for you existing app and create the nginx and system entries to incorporate into your app.

