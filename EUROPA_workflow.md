Europa usage
---------

Starting the robot
----

- check the accu of the robot and camera
- turn on both plugs on the front side
- wait till the computer powers on, run the europa-commander
- on the tabs `auto` and `test` turn everything off
- click `start all`
- check watchdog if everything is running
- start the visualizer for bumblebee
- take the robot where you need
- start `eu-logger` in the `log` tab
- stop `eu-logger` once got the needed data

Processing the dataset
----

- copy the log to your machine to folder `logs`
- start virtual machine to run europa-related stuff
- unzip the log file: `gunzip *.alog.gz`
- create `img` directory in the recent log folder
- cd into `img` directory
- write rectified images and their timestamps:
  `extractBumblebee -F jpg -t timestamps.txt -r ../*.alog`
- prepare the alog file by transfering it from moos format to carmen format:
`moos2carmen *.alog`
- run the mapper on the carmen log:
`test_mapper -g -ini ~/workspace/europa/mapper/mapper/mapper.ini *-carmen.log`
- after we have got result we want to make it consistent with gps by using this command:
`globallyConsistentGm2dl -i 20 -o result-gps.gm2dl result.gm2dl *-carmen.log`
