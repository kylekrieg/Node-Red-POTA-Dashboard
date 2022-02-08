POTA Dashboard & Notifier
=============

Flow to Notify for POTA operators or locations

### About

This is your project's README.md file. It helps users understand what your
project does, how to use it and anything else they may need to know.


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
