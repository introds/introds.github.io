# UFO-tracker Report


## General description

UFO tracker is an application to track and predict UFO locations based on over 80,000 UFO sighting reports. We also analysed the data to get different statistics and insights out of all these reports.

## Tools used

* Python
* JacaScript
* Angular

## What we did

Jukka-Pekka was mostly in charge of the web/js/angular side of the project, while Tomi and Thang took mostly care of the data handling side.

### Cleaning and polishing (notebooks/ufo-cleaning.ipynb)

We used Panda and Numpy Python libraries to read in and handle the data. The data had to be cleaned first; we dropped columns that were not providing any relevant information for our purposes (date posted, duration in hrs/min since we have one in seconds). There was some city, country and state info missing, using some interpolations we filled around 8k out of 12k missing countries. Then we converted date info to datetime objects separating hour, day, month and year into own columns for direct accessing. There were around 1k wrong format datetime which we dropped. We wrote the cleaned data to new csv file for the data handling.

### Data exploration (notebooks/ufo-exploration.ipynb and notebooks/ufo_description_processing.ipynb)

Reading the data from cleaned file we did some quite straightforward plotting to reveal insights of the data. We exposed the top countries regarding sightings (USA having the big majority of all the sightings) and the top states of USA (california having more than twice the amount of its followers; florida, washington etc.). We plotted UFO sights per year (increased massively since 1990), per month (peaking in august/winter), per day (peaking in the beginning and middle of month) and per hour (most sightings in evening/night). We plotted most commonly described shapes top 5 being light, triangle, circle, fireball and unkown.

We did some text analysing on the freely written descriptions made by the one who claimed to see UFOs in a typical text handling manner: Everything into lower caps, removing punctuations and stopwords and stemming everything. This was then written into a text file inorder to get tf/idf for the words and plotting the highest scoring ones into a wordcloud.

UFO location prediction is done using K-means clustering calculating multiple "best" locations for UFO sightings.

### The map app

Getting locations from the reports, we show UFO sights on the map per year or as a total count from 1906 to 2014 (adjustable by slider). Current probability and "best" location to see a UFO on a selected date is provided as well based on K-means clustering.

## Lacks and possible improvements

* Take airport and military base locations into account (lower the probability for "real UFO sighting" if close to airport, analyse correlation with old UFO sightings)
* Take present weather info into account for predictions and analyse old weather data and see if correlations with testimonies and weather phenomena
* UFO reports are based on subjective testimonies without knowledge of subjects mental health ect, no guarantee of prediction accuracy

## The team

* Thang Nguyen
* Tomi Rikander
* Jukka-Pekka Seppänen
