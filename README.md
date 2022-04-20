# TennisShots
Based on Swing Vision (computer vision)  shot by shot data. Manual and semi-automatic correction of the data by using the score evolution (either from Video_correction script or from a Tkinter client app). Analysis of the data with the "shot_analysis" script (under development).

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
