# Celestial Visibility & Observational Planning Tool

This Python-based tool calculates the **nighttime visibility windows** for specific celestial bodies from a given geographic location over a defined period (e.g., a full calendar year). By intersecting the object's coordinates with solar altitude data, the script determines the precise Universal Time (UT) intervals available for observation.

## Key Features
* **Coordinate Mapping**: Uses `astropy.coordinates` to handle Right Ascension (RA) and Declination (Dec) for celestial bodies.
* **Sidereal Logic**: Custom implementation of functions to calculate sidereal rising and setting times based on observer latitude.
* **Visibility Intersection**: Advanced algorithm to find the overlap between the "astronomical night" (Sun below the horizon) and the period when the target object is above the horizon.
* **Universal Time Conversion**: Converts sidereal intervals into practical UT windows for observational scheduling.
* **Automated Reporting**: Generates a structured `visibilidad.csv` file containing daily visibility intervals and total observational duration for 365 days.

##  Tech Stack
* **Language**: Python 3.x
* **Core Libraries**: 
    * `Astropy`: For time scales, coordinate frames, units, and table management.
    * `NumPy`: For efficient numerical array handling and date ranges.

##  How it Works
1. **Initial Data**: Define the target object's RA/Dec and the observer's Latitude/Longitude.
2. **Solar Calculation**: The script fetches the Sun's position for every date in the range using `get_sun`.
3. **Sidereal Processing**: It calculates the sidereal time of rising and setting for both the Sun and the target.
4. **Time Windowing**: It computes the intersection of "night" and "object-up" times, converting the result to decimal UT hours.
5. **Output**: Results are exported to a CSV table for further analysis or telescope scheduling.

##  Usage Example
```python
# Configure your target and location
ra = Angle('19h59m36s')
dec = Angle('22d43m16s')
lat = Angle('28d18m00s')
lon = Angle('-16d30m35s')

# The script outputs visibility intervals and total duration
