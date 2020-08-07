# FatigueBan-Preprocessing

Wrangled and pre-processed Crash statistics from Vic roads accounting for accidents happened all over victoria in past 5 years. We are only 
interested in the accident caused due to fatigued driving. The data was wrangled, all the unnecessary columns were excluded from the dataframes, 
the date and timing of the accidents were corrected, the accidents were filtered according to the bilogical sleep times, since those were notorious for
accidents due to fatigue. 
Since there is still no way of detecting fatigue related accidents, also the police do not
have any training in regard to this, hence this goes crash type data does not get
reported and we face data inadequacy. We have used the following method to identify
fatigue related accidents from other accidents:
- Excluded all crashes involved with BAC higher than 0.05g/100ml.
- Excluded accidents involving pedestrians.
- Included head-on crashes, included crashes between midnight to 6AM and 2pm to 4pm.
- Excluded the overtaking crashes.
- Included vehicle performed manoeuvre which resulted in loss of focus due to fatigue,
vehicle travelled into the incorrect side of the road, vehicle involved in head-on
collisions, vehicle ran off the straight road or off the road to outside of a curve, etc.

Hence considering these factors we will make assumptions in our
incomplete datasets to differentiate drowsy related accidents from other accidents. 

After the wrangling and preprocessing, I wanted to reduce the accidents, there had been over 75000 accidents in the span of 5 years in victoria, after filtering it out 
for only fatigued accidents, we still had aroung 20,000 entries to work with. 
My goal was to used these accident spots to alert the drivers of the accident zones around them, so I decided to condense them to even few spots, by forming clusters, 
for this I first decided to use the K-means algorithm to cluster these accidents as the data is unsupervised, as this did work out well, I moved on to used DBSCAN 
(Density-based spatial clustering of applications with noise) this worked extra ordinarily as this algorithm did extraordinary in getting rid of the noise.
I set a radius of 500m and an exception that no less than 10 accidents in the cluster would be significant, anything less than 10 accident per 500m radius was termed noise and 
got sacked. Using this algorithm I formed three severities for the drivers to choose from : 
- Low - Consists of 3 accidents per cluster
- Medium - Consists of 5 accidents per cluster
- High - Consists of 10 accidents per cluster


Dataset - https://vicroadsopendata-vicroadsmaps.opendata.arcgis.com/  
