# GISProject

Ok so these are owen edits 

First, I took the Crime data set and split it into Day and night, by doing so I had to create a new feature class in the crime incidents called "Hour" so i could split each crime (when it was reported) and classify it into what hour it belonged to. This comes from "REPORT_DAT" feature class. From there it put it into hour categories 0-23 representing hours of the day.

From there, I split it into 2 more layers: 
  Crime at Night which is Hour >= 20 OR Hour <= 6  (8pm-6am)
  Crime at Day which is the opposite (6am-8pm)

From there, in the CrimeAtNight feature class i used the "Near" tool to determine the distance of each crime in US Feet of how far it was away from a streetlamp, identified by NEAR_DIST
    I went to Statistics and found the mean crime distance away is 11.86 feet away from a streetlamp
      Min: .38 ft    Max: 418.02 ft   SD: 11.80
Feel Free to Check all of these because yes they look weird but they are right

I then created a Feature class called "Distance_Class" to place each distance into 3 categories: Very Close, Moderate, and Far

I then realized that I don't know how much the light distance from a streetlamp would reach, so I opened up Street Lights and found 5,000 inactive, so created a new "Active_Street_Lights" Layer to get rid of the inactive ones. (Didn't update the distances from old lamps because that will slide)

I also found Pole Height is the best determiner for seeing how far light travels with a street lamp, but in our dataset it is "Text" type so I am unable to run statistics other than count of the height. I posted the bar graph hopefully but if not, then 69.7% of all the lamps are either 30 or 35 feet tall.

<img width="1637" height="423" alt="image" src="https://github.com/user-attachments/assets/3316c5d2-c78b-4862-aa54-7164fc8be0c0" />
^^^^^^^^^^^That is the image hopefully it works

Here is the image of the total spread of height: <img width="192" height="239" alt="image" src="https://github.com/user-attachments/assets/ec3929d8-ab27-4434-add2-e041456895b5" />

It's probably possible to individually separate the poles and determine which is "Close" vs "moderate" vs "far" based on lighting but that seems tedious and unnecessary for this assignment

So now i searched up how far does a 35 foot pole light spread, considering that it is 50% of the height of streetlamps in DC. However after some research now I think most of them are on Highways or main roads, where potentially less crime is going to happen anyways FUCK but we're pushing on with this assumption because we're undergrads and this doesn't matter.

a 35 foot tall lamp post can reach fully about 52.5 feet away on the ground as lamp posts can usually reach about 1.5x their height.

So, I am setting parameters "Very Close" to about 15 feet. "Moderately Close" from 15 feet to 35 feet. and "Far" from 35 feet to 52.5 feet. Past that is "Too Far for Light"

I made these into Unique symbols in symbology to visualize the count and location of where the crime at night is taking place and proximity to an active street light. I find the yellow to be challenging to see but can't think of another good color to use.

Up to here will be uploaded as FinalProjectCleaning1

BREAK ----------------------------------------------------------------------------------------------------------------



