POTA Dashboard & Notifier
=============

# Scope 

This flow does following items and refreshes every 60 seconds
- Displays # of active POTA spots by total, band and mode
- Displays the location of each POTA spot on a map by band and mode
- Dispalys a list of all the active POTA spots
- Simple notification via email and local audio of spots by activator, park or location discription*

* More notifications can be added like text, telegram, discord, etc by doing a bit of research and adding the correct configurations

# Pre Loading Configuration

These flows require sqlite3 to be installed on your system.  At a terminal command prompt issue the command (everything after the $).
```
sudo apt-get install sqlite3
```
This will install sqlite3 on to your raspberry pi.

Now we need to build the POTA tables in the database. 

At the terminal command prompt User (pi) type the following (everything after the $).
```
sqlite3 pota
```
This will create a database named "pota" and drop you into the database.

Now we have to create a tables within the pota database.

At the sqlite> prompt, copy everything below down to the semicolon and paste into the database.  When done, hit <enter>  This will create a table called qsos and a table named spots.


```
CREATE TABLE validparksdesignator(
  "designator" TEXT type UNIQUE
);
CREATE TABLE designatoralert(
 "designator" TEXT type UNIQUE
);
CREATE TABLE callsignalert(
 "callsign" TEXT type UNIQUE
);
CREATE TABLE parkalert(
 "park" TEXT type UNIQUE
);
CREATE TABLE huntedparks(
  "DXCCEntity" TEXT,
  "Location" TEXT,
  "HASC" TEXT,
  "Reference" TEXT type UNIQUE,
  "ParkName" TEXT,
  "FirstQSODate" TEXT,
  "QSOs" INTEGER
);
CREATE TABLE locdescalert(
 "locdesc" TEXT type UNIQUE
);
```
To verify, type .schema at the carrot (>) prompt to confirm your database structure.  You should see everything above.
```
.schema
```
Type .exit to exit out of the database and return to the Pi command prompt.
```
.exit 
```
Your Node Red local pota database is now created and ready to go.  Now configure the properties of the SQLite node (you installed via pallet manager) to create (or confirm) the node is pointing to the pota database.  The database name is case sensitive inside the node properties.  
