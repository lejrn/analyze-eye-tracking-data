# Development ideas


Signals:
Pupil Size Signal: A time series representing the calculated size (e.g., area or diameter) of the pupil for each eye, frame by frame. This is the main signal you'll be filtering and analyzing.

Eye Openness Signal (Hint for Blinks): A time series indicating how open the eye is, likely derived from the vertical distance between upper and lower eyelid landmarks. This is used specifically for blink detection.

(Optional) Iris Diameter Signal: If implementing the bonus conversion to mm, you'd calculate the iris diameter (distance between landmarks 6 and 11) over time.

Signal quality:
1. Valid face detected frames - how many frames in which the face is detected are
2. Missing landmarks detected - how many missing landmarks are there (while the frame is marked as OK)
3. Mean Noise (Jitter) - mean of each landmarks' time series (preferrably after cleaning blinks), then mean of all landmarks' noise
4. Valid non blink frames - How many frames of blinkings were dropped out / total frames
5. Outlier (spikes) values detected frames - how many frames in which there are spikes, sum of all variables


Clean Data Steps:

1. Remove all non OK frames
2. Clear blinks
3. Calculate Outliers
4. Clear outliers
5. Calculate Noise
6. Smoothen data
7. Interpolate missing frames (?)

biomarkers or metrics I should use to reduce noise:

V - blinking: the distance between upper eyelid (landmark 3) to lower eyelid (landmark 19) is smaller than the pupil size > the eye is shut or in the middle of it. maybe we can assume a less strict size to determine that it's a blink. Maybe it could be indicated by the area of the eye ball, cuz it if's smaller, then it means that the eye is blinking.

V - Constriction latency: Time from ... flash‑on ... to ... the moment the pupil starts shrinking. This is the time duration for the eye to respond with constriction.

In order to find the constriction latency, we need to measure the starting size of the pupil, and determine the threshold from which, the pupil's size is definietely changing (not just a noise).

V - Total constriction: Size drop from constriction start to the tightest pupil point.

V - Constriction velocity: How fast the constirction goes.

V- In order to find the constriction velocity, we need to set a threshold or find it of the tightest pupil size, once it's stable enough. then measure the time difference. 




Noise:
1. if interpolated area that is larger than the pupil's average eye size, then it's noise and needs to be filtered out
2. if the distance between landmarks of the pupil to the center are all bigger or smaller than the average radius, then it's noise.
Which one would be quicker to calculate? the area of the polygon, or the distance of each of the radiuses? I think that the first one, since it's anyway being calculated, then it's easier to just run another condition to see if it's exploding or not.


3. Calculate the variance or the correlation between the left eye and right eye center position changes, so if one is more steady, we can conclude that the other isn't so steady.
