# EDL file parser

## User story

User is an editor in a TV station, and he wants to use export (EDL file) from his editing software to generate a list of used audio clips + their duration.

* only audio clips are relevant for this
* if the audio clip is played on both channels (left, right) at the same time, they count as one
* keep the order of the audio clips
* ignore muted tracks
* round the duration up to the nearest second

## Interface and input
A simple webpage with one form - one textfield for episode name + upload of the EDL file

* episode name (text)
* EDL file (file upload)

## Output 
Parse the following information from the file:
* clip file name (without .L or .R)
* parse Album code from filename, if possible (see below)
* parse Track number from filename, if possible (see below)
* parse Track name from filename, if possible (see below)
* clip duration, in m:ss, rounded up to the nearest second

Show parsed output as a table:

| File name                        | Album code | Track no | Track name               | Duration [m:ss]       |
| -------------------------------- | ---------- | --------:| ------------------------ |----------------------:| 
| ARTFCD69_6-Android-01            | ARTFCD69   |        6 | Android                  |                  3:31 | 
| 101DOM19_6-Artificial_Tears-01   | 101DOM19   |        6 | Artificial Tears         |                 10:41 | 
| sometrack.mp3                    |            |          | sometrack.mp3            |                  0:11 | 
| ARTFCD69_6-Android-01            | ARTFCD69   |        6 | Android                  |                  0:41 |

## Implementation

* use PHP 7.1.3
* if you use any framework, it has to be Laravel 5.6.2
* if you use any 3rd party libraries, you have to use Composer
* keep the parser logic separate from the interface. Parser should be reusable in another application without changes.
* use local Git repository. Make frequent commits. Then make a pull request to this repository when you're ready
* ask questions by email to marek.polan at hudebnibanka.cz