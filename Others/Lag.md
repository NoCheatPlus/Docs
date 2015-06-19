# Server
A small list of latency issues that can happen on the server side

## TPS - Ticks per second
`Imagine you have an alarm which rings every minute. Every time the alarm goes off its a "tick". Now during each minute you have to do some work. Sometimes this can be simple stuff like picking up books from your desk and placing them on your bed and sometimes it can be very difficult stuff like cleaning your desk completely. Similarly your server has a concept of ticks, and during each tick it does stuff like spawn mobs, load chunks, perform physics checks etc.

So when you have small amounts of work to do, you can finish it in less than a minute and spend the rest of the time relaxing but when you get too much work and can't finish it in a minute you need to delay the alarm clock meaning now a tick isn't once every minute, its taking more than a minute. Similarly your server also relaxes when it finishes in less than its ticking interval and when it can't finish its work in time it has to extend the tick time too.

Normally your server ticks 20 times a second, like how you were ticking once a minute.
When you can't keep up with your work, you degrade to less than 1 tick per minute, similarly your server degrades to less than 20 ticks per second.

Usually this will be met by an increase in cpu usage because the server is constantly doing work (not in all cases though!)`
[@ammar2 at SpigotMC](https://www.spigotmc.org/threads/what-is-tps.4277/#post-43925)

So in short: If your server cant finish all the scheduled tasks in 20 ticks or less you will feel latency in form of delayed blockbreaking, movement and other.

## Network
Game experience could suffer because of lost/delayed packets if your server:  
* Has a bad/defect network card (hardware) that cant process all packets properly
* Is hooked on a bad internet provider that fails to handle your network traffic properly
* Has a bad operating system which isn't properly supporting everything
* Is hooked on a busy local network (Example: At home you have 5 other clients that download/upload on high-speed)
* Is running other background processes that overload your network traffic

# Client
A small list of latency issues that can happen on the Minecraft client

## TPS - Ticks per second
Just as the server, the client also needs to finish a lot of other tasks in 20 ticks.

## FPS - Frames per second
As you may know in order to create a moving picture you need to quickly display a lot of pictures (frames) one after an other. A computer works pretty similar because it also displays 60 (or more) frames per second to make you think that there is actually movement in that picture.

* A basic Computer monitor can output a maximum of 60 Mhz while a profersional one can reach 120 Mhz (Mhz=FPS).
* You wont feel any performance improvements if your GPU surpasses your monitors maximum Mhz, all it does is probably shorten your GPUs life time.
* If your GPU fails to keep up with the game renderer (too many particles, too much chunks loaded at once and much more...) you will feel latency.
* VSync or VerticalSync tries to synchronise your GPU with the monitor by making the GPU only process as much FPS as the monitor can handle.

[Monitor & TV Refresh Rates as Fast As Possible]
[FreeSync and VSync explanation]

## Network
Latency can also occur if the client:
* Has a bad/defect network card (hardware) that cant process all packets properly
* Is hooked on a bad internet provider that fails to handle your network traffic properly
* Has a bad operating system which isn't properly supporting everything
* Is hooked on a busy local network (Example: At home you have 5 other clients that download/upload on high-speed)
* Is running other background processes that overload your network traffic

# Hardware bottlenecks
A small list to explain which hardware is responsible for a curtain type of latency:  

- **TPS**
 - Disk I/O (Hard drive where MC reads/writes data on)
 - CPU (Doing maths and a lot of other required tasks)
 - RAM (MC keeps a lot of data in your random access memory before it drops that data or saves it on your disk)

- **FPS**
 - GPU (Additionally to the TPS list you will also need a good GPU to keep up with the game renderer and display enough frames for a smooth game experience)
 
- **Network**
 - Network card
 - CPU (Yes processing packets requires a CPU)
 - Router (On good ones you can tweak a lot of settings to manage your network traffic properly)
 - Ethernet cable (Try to not host on WiFi if you can avoid it)
 - Internet provider (If you do home hosting: You might need to look up business plans of your internet provider for the best results)
 
[Monitor & TV Refresh Rates as Fast As Possible]:https://www.youtube.com/watch?v=YCWZ_kWTB9w
[FreeSync and VSync explanation]:https://www.youtube.com/watch?v=5Ey-KObDABI