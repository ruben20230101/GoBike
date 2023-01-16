# Ford GoBike System Data (Exploratory Data Analysis)

## Dataset

The selected dataset (Ford GoBike System dataset from 2019) is a dataset that contains information on bike rentals from the Ford GoBike bike sharing system. The dataset includes information such as the start and end station, start and end time, duration of the ride, and user information (e.g., whether the user is a subscriber or a customer, and their birth year). It also contains geospatial information such as the latitude and longitude of the start and end station. It likely covers multiple months, the duration is likely covering a full year or a portion of it in 2019. The dataset may be used to analyze bike rental patterns and user behavior, as well as help city planners and bike sharing companies improve the bike sharing system.

This dataset contains 183,412 rows and 16 columns
Longitude and latitude have 6 digits after the decimal point, which are necessary for accuracy.
All variable names are clear and formatting is consistent.

start_time and end_time are both formatted as objects, convert to DateTime,
station_id (both start and end) are formatted as float64, convert to int64.
Member_birth_year convert from float64 to int64,

Two columns contain outliers: trip_duration and member_birth_year. The former is hard to judge; the user may intentionally have taken the bike for (almost) an entire day, which is the case of the maximum value in the column. This person may also have forgotten to check out and the system logged him/her out automatically at a specific time. Perhaps it was simply a fluke.

All data is from the year 2019, but the member_birth_year ranges from 1878 to 2001. It stands to reason that 99% of all entries over 99 are incorrect. The amount of rows in which the member_birth_year results in an age over 99 represents 0.04% of the data, and therefor its effect can be considered neglible. To streamline KDE plot I decided to remove the values, since these datapoints would have increased the tail and therefor hampered the design while adding minimal information.

## Summary of Findings

<b>Plot 1</b>: countplot generated in the univariate exploration: after generating a day_of_week column, using the first entry of the dataset, the date is 2019-02-28, the day of the week of Thursday, and the value in the day_of_week column is 3, 0 represents Monday in this dataset. The most salient conclusion that can be drawn from this countplot is that this system is predominantly for transportation to and from work, considering that usage is significantly lower durin the weekend.

<b>Plot 2</b>: To further investigate my hypothesis I plotted the distribution of trips between hours of the day and this distribution follows a 9-5 paradigm, with the highest peaks at 17/8/18/9 (respectively), relatively steady in between, and significantly less in the late evening and early morning.

<b>Plot 3</b>: After removing the 0.04% of rows in which the value for member_birth_year is lower than 1920 (therefor, age over 100), plotting the data in a KDE plot, the result is a left-skewed distribution. Due to the fact that cycling is a physical activity that requires a certain degree of physical fitness, it is not surprisingly that KDE plot is negatively skewed. The peak of this KDE plot stretches between late 80's to early 90's: people who were approximately 30 years old at the time of recording, which is in line with the hypythesis that target audience is young professionals.

<b>Plot 4</b>: Encouraging healthy behavior for employees has, especially since COVID, been a common practice within most companies. Considering that the target audience for GoBike is professionals (rather than tourists), it is not surprising to see that over 90% of all users are subscribers.

<b>Plot 5</b>: The lion's share of the users is male.

<b>Plot 6 and 7</b>: There are no outliers for start and end station.

<b>Plot 8</b>: The heatmap shows little correlation between variables except for longitude/latitude/station_id, which makes sense considering they refer to the same concept.

<b>Plot 9</b>: The scatterplot shows a significant variance in trip duration, especially among those born after 1970.

<b>Plot 10</b>: Since there are too many datapoints in the scatterplot to see more than a general trend, I decided to create a heatmap displaying the cumulative number of trips taken during each day of the week per generation (age bins of 20 years) and displaying the exact numbers on the tiles. what becomes clear is how skewed the data is towards those born between 1980-2000.

<b>Plot 11</b>: Diving further in trip duration per day of the week, I created a boxplot to see the IQR of each individual day. Surpisingly, just as a single generation was responsible for the majority of all trips taken, the IQR of trip duration was limited in comparison to its variance.

<b>Plot 12</b>: Trip duration split out by gender shows that trips taken by women take on average longer, but the difference is not significant.

<b>Plot 13</b>: The popularity of specific stations to both start and end is almost identical (9/10), although I was somewhat surprised the correlation was not perfect for the top 10.

<b>Plot 14</b>: That duration and generation were correlated was already established by plot 10, but in this multivariate visualization I wondered whether user type was correlated with either of those two variables. As it turns out, there is no correlation between duration and user type, but there was a noticable difference between the youngest and oldest generation in terms of user type: the oldest generation were predominantly subscribers, the youngest generation customers. There is no data in this dataset that can be used to draw conclusions about this phenomenon, but I hypothesize that is 1) partly to blame on a generation gap and 2) might have something to do with the fact that these systems usually bill via credit card and young people will either have a card that is attached to their parents' bank account or a low credit score due to their lack of a job.

<b>Plot 15</b>: In the final visualization, I compare my variable of interest from two three different perspectives; day of the week, hour, and age of user. The most salient factors in the visualization are the behavior of the youngest and oldest generation, and the gap between weekdays and the weekend.

## Key Insights for Presentation

I did not intent to focus on time-related variables at the start of this project, assuming (other) demographic factors would play a larger role, but as it turns out, age and time were the most interesting variables in this dataset. My presentation will focus discussing the plots related to time-related distributions.
