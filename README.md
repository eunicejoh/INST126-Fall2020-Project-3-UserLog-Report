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
First, we created a general global dictionary that will store each instance of the user log as a list of its attributes (date, time, action, server, and email) with a unique key, that is sorted in chronological order by the date.

### Suspicious Activities
For suspicious activities, the program will compare each list of attributes (value of the global dct) to all others in the global dictionary, and identify when they match five or more times. Consequently, we will know when users have logged in five or more times, and will record their keys in a dictionary specific to "suspicious activities." When a key is added, the total count of suspicious activities will increase by one.

In order to identify users that have logged in between 12 AM and 5 AM, we will use the second attribute in the list of attributes (time) to filter through the global dictionary, and add the resulting keys to the dictionary specific to "suspicious activities." When a key is added, the total count of suspicious activities will increase by one.

### Irresponsible Behaviors
To find irresponsible behaviors - most commonly, forgetting to log out after logging in - we create two dictionaries that sort our global dictionary by their "action" value. (Those with "login" as the action will be sorted into the login dictionary, and "logout" into the "logout" dictionary.) 

### System Glitches
This process largely follows the same as irresponsible behaviors; however, we look for a greater number of logouts than logins, count the total number of occurrences, and note the specifics of each individual case.

### Domain Count 
In order to address the domain count, we filter through the "email" attribute in the values of the global dictionary, splice by the string following the "@" symbol, and create a new dictionary counting the occurrence of each unique domain. 

## Updates

### November 2nd, 2020
Largely deviated from the plan-of-action upon realizing perhaps we don't, to put it in technical terms, necessarily know how to do most of it.

- Instead of making a function specifically for sorting, we will attempt to learn and use the built-in .sorted() function upon further research on Stack Overflow.
- Rather than making a date+time+server+email combined string for suspicious activities, we will simply compare the lists of values (attributes) of the global dictionary to each other (without the time) and note when they occur 5 or more times.
- Last change also applies to irresponsible behavior and system glitches.
