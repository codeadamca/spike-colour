# LEGO Spike Hub and the Colour Sensor

A Python snippet utilizing the LEGO Spike colour sensor, [MicroPython](https://lego.github.io/MINDSTORMS-Robot-Inventor-hub-API/), and the `get_color()` and `wait_for_new_color()` commands.

## Sample Code

This code changes the hub colours based on the colour sensor data:

```py
from mindstorms import MSHub, ColorSensor
from mindstorms.control import wait_for_seconds
from mindstorms.operator import equal_to
import math

hub = MSHub()

color_sensor = ColorSensor('A')

while True:

    color = color_sensor.get_color()

    if equal_to(color, 'red'):

        hub.status_light.on('red')

    elif equal_to(color, 'green'):

        hub.status_light.on('green')

    elif equal_to(color, 'yellow'):

        hub.status_light.on('yellow')

    else:

        hub.status_light.off()
        print(color)

    if hub.left_button.is_pressed() and hub.right_button.is_pressed():

        break

color_sensor.wait_until_color('blue')
hub.status_light.on('blue')

wait_for_seconds(5)

hub.status_light.off()

hub.speaker.beep()
```

This code changes the light on the colour sennsor based on colour sensor data:

```py
from mindstorms import MSHub, Motor, MotorPair, ColorSensor, DistanceSensor, App
from mindstorms.control import wait_for_seconds, wait_until, Timer
from mindstorms.operator import greater_than, greater_than_or_equal_to, less_than, less_than_or_equal_to, equal_to, not_equal_to
import math

hub = MSHub()

color_sensor = ColorSensor('A')

counter = 0

while True:

    if equal_to(counter % 3, 0):

        color_sensor.light_up(100, 0, 0)

    elif equal_to(counter % 3, 1):

        color_sensor.light_up(0, 100, 0)

    elif equal_to(counter % 3, 2):

        color_sensor.light_up(0, 0, 100)

    wait_for_seconds(0.1)

    counter += 1

    if hub.left_button.is_pressed() and hub.right_button.is_pressed():

        color_sensor.light_up(0, 0, 0)
        break

hub.speaker.beep()
```

***

## Repo Resources

* [Visual Studio Code](https://code.visualstudio.com/)
* [MicroPython for LEGO Robot Inventor](https://www.lego.com/en-ca/themes/mindstorms/downloads)
* [LEGO Mindstorms](https://www.lego.com/en-ca/themes/mindstorms)
* [LEGO Mindstorms App for Mac](https://apps.apple.com/us/app/lego-mindstorms-inventor/id1515448947)
* [LEGO Mindstorms App for Android](https://play.google.com/store/apps/details?id=com.lego.retail.mindstorms)
* [LEGO Mindstorms App for Windows](https://www.microsoft.com/store/apps/9N7GN3KC2GK6)

<a href="https://codeadam.ca">
<img src="https://codeadam.ca/images/code-block.png" width="100">
</a>

