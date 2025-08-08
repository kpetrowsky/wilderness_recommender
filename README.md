# My Wilderness Recommendation System
Using k-nearest neighbors to recommend wildernesses to visit based on a liked wilderness

<h3>Introduction</h3>
Every summer I like to go out on a backpacking trip in the wilderness. My preferences are peculiar, so it can be a bit of work to find the ideal location, and of course, I worry about missed opportunities. I eventually thought to myself “How great would it be to have a wilderness recommendation system!” I checked my AllTrails app, and it didn’t have one, so I set out to create my own basic recommendation system.

<h3>Data Collection</h3>
I used Chat GPT to generate my model features. I used the wilderness I visited last summer as a reference to refine Chat’s output. Once satisfied, I instructed Chat to generate features for all 154 wildernesses. I was surprised to see typos and duplicates in the generated data, so it was time to move on to data cleaning

<h3>Data Cleaning / Transformation</h3>
I decided to start with three features. (1) camping permit needed, (2) summer traffic, and (3) activities. 
The camping permit feature was transformed into binary values using a lambda function. 
The summer traffic categories were transformed into ordinal numbers on a zero to four scale. 
For the activity feature, I decided on a manual one-hot encoding approach. I first scanned all unique activities at the parks and decided on major categories. This required consolidating some of the activities into a single category like skiing and cross-county skiing. I then created a new column for each category and checked whether the source string contained certain substrings pertaining to that category. If there was a match for any of the substrings one would be returned. Zero was otherwise returned 
Now that all my categorical data was transformed into some form of numerical format, I was ready to start modeling.

<h3>Modeling</h3>
I wanted to see wildernesses like the Jennie Lakes Wilderness, so I decided to use a k-nearest neighbors model with the cosine metric from the skikit learn library. I chose to display the park names of 4 recommendations

<h3>Results</h3>
This recommendation system exceeded my expectations! My recommendations ended up being the Marble Mountain Wilderness, Carson-Iceberg Wilderness, Domeland Wilderness, and the Emigrant Wilderness. I’m planning to visit the Emigrant wilderness this summer, and the Carson-Iceberg wilderness was one of my top alternative picks. I was surprised to see the Domeland wilderness, but I was strongly considering that location for a winter camp. Finally, I hadn’t heard of the Marble Mountain wilderness before, but I looked it up, and it was right up my valley. 

<h3>Next Steps</h3>
I would like to add elevation as a feature. My approach would be rounding or binning the elevation and then normalizing. I would also like to expand my pool to other types like wildlife preserves, state parks, and national forests. Since significant overlap exists between different park types, I’ll probably have a separate system for each type. Finally, I could look to refine the activity categories.
 
