# Python Ship Logbook

This is an implementation of a Ship Logbook Service responsible for receiving, collecting, processing and presenting data from "VDR - Vessel Data Recorders" and making it available for further analysis or storage. The primary goal of a Ship Logbook Service is maintaining an precise log of essential ship instruments readings such as vessel position, speed, heading, engine parameters, rudder movements, communications, alarms and many others. The secondary goal is to provide a way to access this data in a convenient way. For such a task the service provides a "Data Ingestor Service" to receive data from the VRD and a "Data Dashboard Service" to provide access to the data though an dashboard. The services also provides a "Data Disgestor Service" to process the data and make it available for further analysis,  storage or disposal through a API so other services can access it.

## Architecture

The Ship Logbook Service is composed of three main components:

- Data Ingestor Service
- Data Dashboard Service
- Data Disgestor Service

**1) Data Ingestor Service**

The Data Ingestor Service is responsible for receiving data from the VDR and storing it in a database. The Ingestor connects to the VDR through a TCP connection and receives data in the form of NMEA sentences. The Ingestor parses the NMEA sentences and stores the data in a database. As the ship may have issues regarding connectivity, the Ingestor is responsible for keeping trying to connect to the VDR and each time it connects it will pull all the data that was not received yet. Readings should be saved in a cronomological order, so the Ingestor should be able to detect if readings are out of order, it should be able to detect duplicate entries. Readings should be saved to database in a way that it is easy to query them by time range, by type of reading, by ship, by ship and time range, by ship and type of reading, by ship, type of reading and time range. The Ingestor should be able to detect if the VDR is sending data that is not in the NMEA format and alert developers. 

**2) Data Dashboard Service**

The Data Dashboard Service is responsible for providing a dashboard to access the data. The dashboard should be able to show the data in a way that is easy to understand and navigate. The dashboard should be compatible with desktop and mobile browsers, it also should have a responsive design. Graphic interface should be easy to understand and should be as clear as possible. The dashboard should permit to choose from all available ships, may they be active or inactive. Active meaning when the VDR - Vessel Data Recorder is turned on, and inactive meaning when the VDR is turned off. The dashboard should inform if any expected reading from VDR is not present, and alert developers. 

**3) Data Disgestor Service**

The Data Disgestor Service is responsible to ...

