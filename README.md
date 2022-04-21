# TennisShots
Based on Swing Vision (computer vision)  shot by shot data.

Manual and semi-automatic correction of the data by using the score evolution (either from Video_correction script or from a Tkinter client app).

Analysis of the data with the "shot_analysis" script (under development).

## 1 - Collecting data from Swing Vision
https://swing.tennis/
- The data is collected from the CSV exported after processing the video of a match under the app and exporting the results into an Excel file
- The file will contain the following data for each shot of each point of the match:
    - Time
    - Shot index
    - x,y,z coordinates of the ball when Hit by the player
    - x,y coordinates of the Bounce for this shot
    - Stroke type of the player (serve, forehand, backahnd, fh volley, bh volley, overhead)
    - Result (in, out, net, let)
    - Speed (avg speed of the ball for this shot)
    - Spin (Flat, Slice...)
    ..

## 2 - Correcting the data 
Unfortunately the data is not 100% accurate and it can totally change the analysis of a shot/point.
The best example is a ball OUT counted as IN.
The potential mistakes include:
- the result of the shot incorrectly identified (for example a ball OUT counted as IN).
- the identification of the players might have been swapped for this point.
- some missing shots
In order to correct this we use 2 data source:
- the official score evolution which can check if the result of the point as identified by the shot by data is correct
- the video

The data can be corrected either from
- a Tkinter client app 
 ![](https://github.com/damienld/TennisShots/blob/main/img/readme/tkinter.png)
- the "Video_correction" notebook with IWidget and plotly dataviz
 ![](https://github.com/damienld/TennisShots/blob/main/img/readme/video_correction.png)

At this stage, the score and service information have been fully added.

## 3 - Generating Stats
Some useful data can be manually or semi-automatically added:
- a Winner/ Unforced Error/ Forced Error stat for each ending shot of each point (the goal would be to make a model to automatically identify this data at one point)

Each point/shot is processed in order to bring some useful data analytics stats:
- rally length
- service zones: outside/body/T
- shot direction : cross/middle/down the line/inside out/inside in/inside middle   
- pass/dropshot status are added to each shot identified as such

Then an excel file is generated to compile/group the different stats (winners/errors/played/lost/won) for each shot type.
For example:
- 1st SERVICE to T (winners/missed/points won/points lost)
- FH down the line RETURN behind 1st serve (winners/missed/points won/points lost)
- FH down the line (on serve) between 5-8th shot (winners/missed/points won/points lost)
- Slice between 5-8th shot (winners/missed/points won/points lost) 
...
Also:
- Points won by rally length 

## 4 - Data Viz
A notebook "shot_analysis" is under development in order to display some useful dataviz (using plotly).
A few examples:
![](https://github.com/damienld/TennisShots/blob/main/img/readme/shot_analysis1.png)
![](https://github.com/damienld/TennisShots/blob/main/img/readme/shot_analysis2.png)
![](https://github.com/damienld/TennisShots/blob/main/img/readme/shot_analysis3.png)
![](https://github.com/damienld/TennisShots/blob/main/img/readme/shot_analysis4.png)
![](https://github.com/damienld/TennisShots/blob/main/img/readme/shot_analysis5.png)

## 6 - Interactive Dashboard
A Dash interactive dashboard is currently being developped.
It would allow to visualize/filter specific shot sequences. 