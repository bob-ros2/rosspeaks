# RosSpeaks

A simple generic TTS speak simulator ROS Node. Other to be used Speech 
engines can also be configured.

## Installation Prerequisites

One or both of these are pre installed
- espeak
- spd-say

```bash
# installation
sudo apt-get update
# espeak
sudo apt-get install espeak
# spd-say
sudo apt-get install speech-dispatcher
```

## Setup Node ##

```bash
# run in your ros2_ws/src folder
git clone https://gitlab.com/bob-ros2/rosspeaks.git
cd ..
colcon build
. install/setup.bash
```

## ROS Node rosspeaks

### Usage

```bash
# start the node.
ros2 run rosspeaks speak.py
```

### Node Parameter

> ~pitch (int, default: 60)\
Pitch of voice.

> ~rate (int, default: 90)\
Rate of voice.

> ~lang (string, default: "en+f3")\
Language type. The value format depends on the used speech engine.

> ~level (int, default: 70)\
Level of voice.

> ~suppress (Bool, default: False)\
Possibility to suppress the speak execution. If True all new
messages are discarded until it's set back to False.

> ~exec (string, default: "espeak")\
To be used speach executable. Integrated speech engines 
are 'espeak' and 'spdsay'.\
If providing a custom executable it will be 
called in the followng way:\
script \<pitch\> \<rate\> \<lang\> \<level\> \<text\>

### Subscribed Topics

> ~speak (std_msgs/String)\
Text to speak. For better control use the action if a finished 
feedback is needed.

### Published Topics

> ~speaking (std_msgs/Bool)\
Flag which indicates if speaking is ongoing. The message is letched to see 
the last state at any time.

### Actions

> ~speak\
Perfoms speaking. The action ends when speaking has finished. 
See [action/Speaking.action](action/Speaking.action) for details.

## Dynamic Reconfigure Parameter
> ~pitch\
 ~rate\
 ~lang\
 ~level\
 ~suppress\
 ~exec

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.\
Please make sure to update tests as appropriate.

## License

[Apache2.0](https://www.apache.org/licenses/LICENSE-2.0)