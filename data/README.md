# Data
-   **ERGAST API**: The Ergast API is a free, open-source web service that provides historical Formula 1 race data from 1950 to 2024, including details on races, drivers, constructors, results, qualifying, and lap times. In this project, we’re using that same structured Ergast dataset via its Kaggle export. 

# Codebook for Dataset (all datasets)

## Variable Names and Descriptions:
**Circuits**
 - circuitId: Unique circuit identifier
 - circuitRef: Short reference name for the circuit
 - name: Official circuit name
 - location: City or locality of the circuit
 - country: Country where circuit is located
 - lat: Latitude coordinate
 - lng: Longitude coordinate
 - alt: Altitude above sea level (may be null)
 - url: Wikipedia or official reference link

**Drivers**
 - driverId: Unique driver identifier
 - driverRef: Short reference name
 - number: Permanent car number of the driver
 - code: 3-letter driver code (e.g., VER, HAM)
 - forename: Driver’s first name
 - surname: Driver’s last name
 - dob: Date of birth
 - nationality: Driver’s nationality
 - url: Wikipedia or official link

**Constructors**
 - constructorId: Unique constructor (team) identifier
 - constructorRef: Short reference name
 - name: Full constructor name
 - nationality: Team nationality
 - url: Wikipedia or official team page

**Results**
 - resultId: Unique result identifier
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - constructorId: Linked constructor ID
 - number: Car number used in race
 - grid: Starting grid position
 - position: Finishing position
 - positionText: Textual representation of position (e.g., R for retired)
 - positionOrder: Numeric order for classification
 - points: Points scored in race
 - laps: Number of laps completed
 - time: Race time string (e.g., 1:36:23.456)
 - milliseconds: Race time in milliseconds
 - fastestLap: Lap number of fastest lap
 - rank: Rank of fastest lap (1 = fastest)
 - fastestLapTime: Time of fastest lap
 - fastestLapSpeed: Average speed during fastest lap
 - statusId: Linked race status code

**Races**
 - raceId: Unique race identifier
 - year: Year of race
 - round: Round number in that season
 - circuitId: Linked circuit ID
 - name: Grand Prix name
 - date: Race date
 - time: Start time (UTC)
 - url: Wikipedia link
 - fp1_date/fp2_date/fp3_date/qualify_date/sprint_date: Session dates (if available)
 - fp1_time/fp2_time/fp3_time/qualify_time/sprint_time: Session times (if available)

**Qualifying**
 - qualifyId: Unique qualifying session identifier
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - constructorId: Linked constructor ID
 - number: Car number
 - position: Qualifying position
 - q1/q2/q3: Recorded times in qualifying rounds 1–3

**Lap Times**
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - lap: Lap number
 - position: Driver position at that lap
 - time: Lap time (HH:MM:SS.mmm)
 - milliseconds: Lap time in milliseconds

**Pit Stops**
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - stop: Pit stop sequence number
 - lap: Lap when pit stop occurred
 - time: Timestamp of pit entry
 - duration: Duration string of stop (e.g., “24.1”)
 - milliseconds: Duration in milliseconds

**Constructor Results**
 - constructorResultsId: Unique ID for constructor race result
 - raceId: Linked race ID
 - constructorId: Linked constructor ID
 - points: Points earned by constructor
 - status: Status (e.g., “Finished”, “Disqualified”)

**Constructor Standings**
 - constructorStandingsId: Unique ID for standings entry
 - raceId: Linked race ID
 - constructorId: Linked constructor ID
 - points: Total season points so far
 - position: Current position in constructor championship
 - wins: Total wins so far

**Driver Standings**
 - driverStandingsId: Unique ID for standings entry
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - points: Total season points so far
 - position: Current position in driver championship
 - wins: Total wins so far

**Sprint Results**
 - resultId: Unique result identifier for sprint race
 - raceId: Linked race ID
 - driverId: Linked driver ID
 - constructorId: Linked constructor ID
 - grid: Starting grid position in sprint
 - position: Finishing position in sprint
 - points: Points earned in sprint
 - laps: Number of laps completed
 - time: Sprint duration
 - milliseconds: Duration in ms
 - fastestLap: Lap number of fastest lap in sprint
 - statusId: Linked status code

**Seasons**
 - year: Season year
 - url: Wikipedia or official link

**Status**
 - statusId: Unique identifier for finish status
 - status: Description (e.g., “Finished”, “Accident”, “Gearbox”)





