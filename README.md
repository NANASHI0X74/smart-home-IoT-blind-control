# smart-home-IoT-blind-control
A solution for controlling and configuring my blind controls at home via http with an esp32 devkit.

# Problem description
I have blind controls at home with two physical buttons on them each used to open or shut them. I want to be able to conrtol all of them individually or simultaneously just from my phone.

More nice to have features which I'd like to add later are:
- I can set times at which they drive up or down via my phone, even when I'm not connected to my home network or any network. The idea would be that I have an app on my phone which saves this information and syncs it with the esp the next time I'm connected to my home network.
- the esp from time to time connects to the internet to look up at what time it gets dark in the area and sets this as the time at which to shut the blinds.
- alternatively, I'll install a brightness sensor outside my window which tells the esp to shut the blinds when the brightness keeps below a threshold for 30 minutes or so.

# Solution sketch
### MVP-ish
- Use esp32 devkit and its GPIO ports
- connect GND of devkit and all blind controls
- connect other sides of buttons each with a GPIO port
- build a REST API server to drive the GPIO ports (probably in c)
- build a web application with buttons as a convenient interface to the REST API (optional. I want to be able to send simple requests just by going to specific URLs in my browser anyway instead of clicking on buttons on a webpage)

### Nice to have
- esp32 should be able to save specific times at which blinds should be shut and opened (does it have a decent RTC? Do I need an external one? How to best schedule the automatic GPIO driving on the chip?)
- esp32 should be able to tell when it gets dark and automatically close the blinds

# Tools I want to use
### definitely
- espressif esp32 wifi chip 
- [espressif IoT development framework](https://github.com/espressif/esp-idf) for developing a RESTful API server controlling GPIO ports to bypass the buttons on the blind controls
- [Google's Project Polymer](https://www.polymer-project.org/) for developing the frontend side

### maybe
- flutter or plain old android APIs with Kotlin if I want to develop a mobile app for my phone. Maybe I'll also build the web application with flutter at some stage
- Qt and/or QML would also be an option for frontend/GUI development (can I use those to build android apps? 🤔)
