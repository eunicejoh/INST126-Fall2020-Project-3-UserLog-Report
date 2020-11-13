# INST126-Fall 2020
## Project 3: User Log Report
### Group Members: Eunice Oh, Ady Weng

## Overview
In most professional working environments, digital activities are recorded through the use of log files.
We were given the activities of 50 users over the course of one month (May 2020) and tasked to analyze the
given log file and generate an automated report consisting of 4 important insights:
- Suspicious Activites
- Irresponsible Behaviors
- System Glitches
- Domain Count

Subsequently, we used Python to write a program that will describe a) the total number of cases for each of the four insights and b) the specific behaviors of each user that contributed to each of the four insights (e.g., the specific occurrences during which an user was involved in suspicious behaviors), both in the form of a formatted report.

## How It Works

### General
First, we created a general global dictionary that will store each instance of the user log as a list of its attributes (date, time, action, server, and email) within the key of their date, subsequently sorted from earliest (May 1st) to the lastest (May 30th. Maybe 31st?)

Then, we created another dictionary that sorted the lists within these dictionaries (the values) by their time, chronologically. Then, as is needed, we created more dictionaries that looped through these chronologically sorted lists, created the key ("date+server+email"), and implemented the values as lists of their relevant attributes.

### Suspicious Activities
For suspicious activities, the program will compare each list of attributes (value of the global dct) to all others in the global dictionary, and identify when they match five or more times. Consequently, we will know when users have logged in five or more times, and will record their keys in a dictionary specific to "suspicious activities." 

In order to identify users that have logged in between 12 AM and 5 AM, we will use the second attribute in the list of attributes (time) to filter through the global dictionary, and add the resulting keys to the dictionary specific to "suspicious activities." When a key is added, the total count of suspicious activities will increase by one.

### Irresponsible Behaviors & System Glitches
To find irresponsible behaviors - most commonly, forgetting to log out after logging in - we create two dictionaries that sort our global dictionary by their "action" value. (Those with "login" as the action will be sorted into the login dictionary, and "logout" into the "logout" dictionary.) The values of the two dictionaries (lists including "date," "server," and "email") will then be directly compared to each other; when the length of the values of the login dictionary are greater than that of the logout dictionary, the key will be stored in the irresponsible behavior dictionary. If the length of the values of the logout dictionary are greater, than they are stored in the systems glitches dictionary.

### Domain Count 
In order to address the domain count, we filter through the "email" attribute in the values of the global dictionary, splice by the string following the "@" symbol, and create a new dictionary counting the occurrence of each unique domain. 

## Installation
Kindly install Jupyter Lab or Jupyter Notebook. Please have a userlog.log file on hand, within the relevant folder. Then, run the ipynb file in a new Jupyter Lab tab. Enjoy!

## Updates

### November 2nd, 2020
Largely deviated from the plan-of-action upon realizing perhaps we don't, to put it in technical terms, necessarily know how to do most of it.

- Instead of making a function specifically for sorting, we will attempt to learn and use the built-in .sorted() function upon further research on Stack Overflow.
- Rather than making a date+time+server+email combined string for suspicious activities, we will simply compare the lists of values (attributes) of the global dictionary to each other (without the time) and note when they occur 5 or more times.
- Last change also applies to irresponsible behavior and system glitches.
- The updated "writing the report" function is detailed in the aforementioned section of the README file.

### November 6th, 2020
Once again changed from the plan-of-action:

- Instead of creating a unique key for each individual line, we have instead created a global dictionary that is sorted based on date, and then subsequently sorted that by time. As needed, we have developed lists with keys that represent the necessary attributes (date+server+email), primarily. Subsequently, the keys of these lists are compared to each other, and when they match, another dictionary is created with a list of the relevant lists of attributes.
- This largely accounts for the changed development of the code for all three functions (sus_act(), irr_beh(), and domain_ct()), though the final saw very few changes.

### November 12th, 2020
Last day!

- Some final notes: we have fixed the issue with regards to the date and emails repeating for each individual printed line (see Challenges We've Encountered, 3).
- There will be no grand function for writing the individual reports; instead, they are worked into the functions that also sort and organize the pertinent dictionaries.

## Challenges We've Encountered
Boy have they been plentiful!

The greatest issue encountered was certainly the sorting of each file entry chronologically. While we were able to solve these issues within the suspicious report entry, unfortunately, the irregular behaviors (irresponsible behavior and system glitches) were unable to be resolved prior to the deadline of the program. 

That being said, we did resolve these three errors over the course of the program (at least):

1. Early troubles involved changing the time associated with each line of the log file into an integer that was useful for sorting purposes. While we considered using Python's built-in date and time functions to some extent, we ultimately passed due to unfamiliarity. Therefore, chronologically sorting parts of this program relied heavily on the ability to split the "time" string and turning each of those into an integer. Then, the places (tens place, ones place) were represented by multiplying by their due place values, and the minutes and seconds were represented by dividing by 60 and 3600, respectively. 

2. There was difficulty in counting the number of suspicious cases per user and reporting due to the structure of the programming. Subsequently, we developed a parallel dictionary that ran alongside the iteration of each "date" - which represented each case - and counted upwards. Then, it was printed. We firmly believe that we could have done this more efficiently, but chose to focus on other aspects of the program as well.

3. Finally, when actually writing the reports, we found that iterating through our created dictionaries resulted in the date and email being written alongside every line of the pertinent log files. Therefore, we created two lists "used_emails" and "used_dates" that would ensure that we did not reiterate through their strings once again. This relied on boolean operators.

## Sources

https://docs.python.org/3/howto/sorting.html
