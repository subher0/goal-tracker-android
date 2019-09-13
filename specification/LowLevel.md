## Low level specs

## Base architecture

### Entities

#### Goal
`Goal` contains all the information about a certain goal:
id: (long) - unique id of a goal;
name: (string) - name of a goal;
description: (string) - description of a goal;
timeSpentSeconds: time spent on a goal in seconds;
created: (date) - when goal was created;
updated: (date) - when goal was last updated;
nextReview: (date) - date of a next review;
isFocused: (boolean) - is the goal currently focused;
isLocked: (boolean) - if true this goal cannot be unfocused

#### Schedule
`Schedule` contains schedule of a goal
It is linked with an entity it schedules for through a reference table:
id (long) - unique id of a schedule
fromTime: (long) - milliseconds of a day from which the event starts
toTime: (long) - milliseconds of a day when event is ended
repeatInterval: (int) - days after which to repeatInterval
repeatUntil: (date) - repeat event until day
description: (string) - description of an event
notifyBefore: (long) - seconds to notify the user before the event

#### TimeLog
`TimeLog` is representing a time spent on a certain goal, activity or TODO entry.
It is linked with an entity it logs the time for through a reference table:
id: (long) - unique time log id;
timeSpent: (long) - spent time in units;
timeUnit: (string) - timeUnit;
timeSpentSeconds: (long) - time spent in seconds;
created: (date) - when log was created;

#### TODO
`ToDo` contains all info about TODO entry:
id: (long) - unique id of a TODO entry;
name: (string) - name of a TODO entity;
description: (string) - TODO description;
priority: (int) - priority of a TODO;
timeSpentSeconds: time spent on a TODO entry in seconds;
created: (date) - when TODO was created;
updated: (date) - when TODO was last updated;
due: (date) - deadline of a TODO entry;
isDone: (boolean) - is done;

## Features

### Screens

1st level activities: Goal activity; TODO activity;

#### Main

On main screen user sees last 1st level activity that he was working with

#### Goal activities

List of goals. Every goal displays its name, spent time and days until next review date. 
It must have a button to log time. Goals are ordered by isFocused and lastUpdated.
It also contains a floating button to add a new goal.

#### Goal activity

All information about goal, including all logged time and schedule;

#### Add goal

Form to add a new goal

### Adding goals

Goals are added by tapping a floation button on a Goal activities screen. 
1. After a tap the app navigates to the Add goals screen.
2. After user finished filling out a form he presses the save button.
3. After a save button tap app navigates back to Goal activities screen.

To become focused a goal must have a review date and it must be no later than in 3 months 
and no earlier than in 1 week from the date it is being focused.
After 3 days have passed a goal cannot be unfocused.