# Server
Lag and latency effects on server side.

## TPS - Ticks per second
`Imagine you have an alarm which rings every minute. Every time the alarm goes off its a "tick". Now during each minute you have to do some work. Sometimes this can be simple stuff like picking up books from your desk and placing them on your bed and sometimes it can be very difficult stuff like cleaning your desk completely. Similarly your server has a concept of ticks, and during each tick it does stuff like spawn mobs, load chunks, perform physics checks etc. So when you have small amounts of work to do, you can finish it in less than a minute and spend the rest of the time relaxing but when you get too much work and can't finish it in a minute you need to delay the alarm clock meaning now a tick isn't once every minute, its taking more than a minute. Similarly your server also relaxes when it finishes in less than its ticking interval and when it can't finish its work in time it has to extend the tick time too. Normally your server ticks 20 times a second, like how you were ticking once a minute. When you can't keep up with your work, you degrade to less than 1 tick per minute, similarly your server degrades to less than 20 ticks per second. Usually this will be met by an increase in cpu usage because the server is constantly doing work (not in all cases though!)`
[@ammar2 at SpigotMC](https://www.spigotmc.org/threads/what-is-tps.4277/#post-43925)

So in short: If your server can't keep up 20 ticks per second, you might notice server side lag, by the server responding slower than usual, e.g. broken blocks or players moves arrive later at other players ends, short player freezes might result, machines or entities move/work slightly slower, buttons take longer to activate. For TPS above 16 it probably isn't that much noticeable client-side.

## Network
Game experience could suffer because of lost/delayed packets if your server:  
* Has a bad/defect network card (hardware) that can't process all packets properly.
* Connection quality (provider, WLAN, mobile, routed twice around the world). 
* The operating system might be faulty or have driver problems.
* Is hooked on a busy local network (Example: At home you have 5 other clients that download/upload on high-speed).
* Is running other background processes that overload your network traffic.

# Client
Lag and latency effects on client side.

## TPS - Ticks per second
Just like the server, the client also needs to finish a lot of tasks 20 times a second (20 ticks).

## FPS - Frames per second
As you may know in order to create a moving picture you need to quickly display a lot of pictures (frames) one after an other. A computer works pretty similar because it also displays 60 (or more) frames per second to make you think that there is actually movement in that picture.

* A basic Computer monitor can output a maximum of 60 Hz while a professional one can reach 120 Hz.
* Usually you won't notice any performance improvements if your GPU surpasses your monitors maximum FPS, all it does is probably shorten your GPUs life time.
* If your GPU fails to keep up with the game renderer (too many particles, too much chunks loaded at once and much more...) you will feel lag.
* VSync or VerticalSync tries to synchronize your GPU with the monitor by making the GPU only process as much FPS as the monitor can handle.

* [Monitor & TV Refresh Rates as Fast As Possible]
* [FreeSync and VSync explanation]

## Network
Latency can also occur if the client:
* Has a bad/defect network card (hardware) that can't process all packets properly
* Connection quality (provider, WLAN, mobile, routed twice around the world). 
* The operating system might be faulty or have driver problems.
* Is hooked on a busy local network (Example: At home you have 5 other clients that download/upload on high-speed)
* Is running other background processes that overload your network traffic. Often the upload bandwidth is much lower than the download bandwidth, thus it's much easier to create noticeable lag with uploading stuff.

# Hardware bottlenecks
A small list to explain which hardware is responsible for a curtain type of latency:  

- **TPS**
 - Disk I/O (MC reads/writes map data, plugins might use local databases).
 - CPU (Minecraft uses a lot of single-core CPU power for the primary thread, but initial packet handling and chunk loading may be done asynchronously).
 - RAM (MC keeps a lot of data in your random access memory before it garbage collects it. Garbage collection could have an impact, low ram might crash the server or lead to more intense disk-io).

- **FPS**
 - GPU/GPU drivers (Additionally to the TPS list you will also need a good GPU to keep up with the game renderer and display enough frames for a smooth game experience)
 - CPU
 - RAM (If your client runs out of memory bad things will happen such as: GarbageCollection going crazy, everything gets moved from your RAM to your hard drive, might trigger a OOME-Out Of Memory Error which could crash your computer or make your operating system forcefully close programs, ...)
 
- **Network**
 - Network card
 - CPU (Yes processing packets requires a CPU).
 - Router (On good ones you can tweak a lot of settings to manage your network traffic properly, quality of service).
 - Internet connection (Try to not host on WiFi if you can avoid it).
 - Internet provider (If you do home hosting: You might need to look up business plans of your internet provider for the best results, you do need good uplink and downlink).
 
[Monitor & TV Refresh Rates as Fast As Possible]:https://www.youtube.com/watch?v=YCWZ_kWTB9w
[FreeSync and VSync explanation]:https://www.youtube.com/watch?v=5Ey-KObDABI
