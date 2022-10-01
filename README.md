# EonLabs-Assessment
## My Approach
My approach was quite simple, in that I used the pytrends API to make a request from 2015 until today on hourly interest data given the keyword 'bitcoin'.
Given that I found that Google was quite frugal in regards to giving out bandwidth and I found myself getting rate-limited, I did only a single call to get
hourly data, and manipulated that data locally to derive daily and weekly data. I also had to add a sleep parameter to the pytrends call that would 
create pauses between successive Google Trends API calls to avoid rate-limiting. It seems that pytrends doesn't request all data in a single shot, and rather
does multiple successive calls over certain windows and then appends them before returning it to me. To derive daily data givent the hourly data, I used
a groupby with a custom grouper. There are many ways to group by specific days, but this seemed like the simplest way to group by specific days of specific
months of specific years. The custom grouper takes frequency as a parameter, and passing 'D' would make it so that the df was grouped by specific calendar days.
I repeated this process again from weekly data, only changing the frequency to 'W', which represents weekly, obviously. At this point I was not sure if 
I was supposed to combine it into a single table and file or into separate tables and files, so I did both. Combining them results in a confusing format 
and I would not usually do that, but just incase that was the format you were requesting, I did it anyway. I did all of this in a jupyter notebook, but downloaded
it as both a python script and as a .ipynb file, because I know that in the assessment description you requested a python script. 

## How Long it Took
About 30 minutes to an hour of work, given that I had to get familiar with the pytrends API, and that I kept running into rate-limiting issues.

## Different Approaches, and Final Approach
Basically, the different main difficulties I faced were first initially attempting to make many different API calls for different time windows; hourly,
daily, weekly. As I discussed above, due to rate-limiting issues, settling on only a single call and deriving the following data myself was by far the 
better thing to do, and that is what I ended up doing. As for deriving the data, I had to find a way to group by year, month, day combinations, and then 
year, month, week combinations. I was initially attempting to parse the date time objects and grouping by some mapping of the date field, but then I found 
out you can just specify a custom grouper that takes frequency as a parameter, so I did that instead. As for now converting the data into files, I was 
unsure whether or not one file or multiple files were required, so I made a file where all the tables were appended, and 3 other files with each containing 
a single table. 

## How to Execute
You could execute the .py file as you could a regular script, but I would recommend opening the notebook in a google colab notebook by clicking the 'Open
in Colab' button that will be available at the top of the notebook. Once there, you can just run the notebook cell by cell and observe its behavior. Literally all you have to do is open the ipynb file here on github, and you will immediately see a 'Open in Colab' button on the top of the page.
