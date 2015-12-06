# Client Side Anti Cheat
This topic keeps popping up, thus we need to clarify our position on this kind of idea.

## The Idea

* Have a client-side solution for detecting or preventing cheats.

## Pro

* The client-side is literally forced to be legit.
* Cheat client developers can't possibly bypass checking for checksums of the binaries/jars.
* Obfuscation rules, cheat client developers have an extra hard time finding what to change to bypass stuff.
* Nodus doesn't work anymore.
* Client side binary installers will ensure no tricks can be used.
* Memory scanning allows to do stuff you won't even want to imagine.
* Ridiculous constraints like not running more than two programs at a time will ensure that no one can bypass this.

## Contra Pro

* Things last until you have one capable cheat client developer interested in "bypassing shit". They're as forced to be legit as they're forced to use a vanilla client for a vanilla server.
* Checksums don't really help, they can be found, faked and will finally be forgotten.
* Obfuscation doesn't prevent people altering the Minecraft server into a system capable of running plugins, why would it scare off a cheat client developer who is used to dealing with obfuscated client code in the first place?
* Nodus can still be updated.
* Client side binary installers will be worked around like every single other game installer of the past and present. Truly legit people may fear malware, unwanted data leaking, privacy risks, security risks, and so on.
* Who wants to have their (entire !?) memory scanned? A capable cheat client developer will prefer to remove that feature by altering the software.
* Ridiculous constraints will be either bypassed by capable cheat client developers having a look at your program, or by players not playing on your server, because it's annoying.
* The client altered by a capable cheat client developer will eventually leak, now (almost) all people can use/do it.

## Contra anyway

* Having to install an extra client just for certain servers is a nuisance in general.
* How trustworthy is such a software, be it a binary installer or just altered obfuscated jar files?
* The more intrusive a software is and the more special things it can do...
 * ...the more likely security holes will open.
 * ...the more likely it'll be an actual risk to your data (privacy, passwords, pictures).
 * ...the more likely no one will have a clue what the software actually is doing.
 * ...the more likely you'll bungle the EULA for users from Tonga and might even get dragged to court for distributing malware.
* The more such is used, the more cheat client developers will have a look.
* The less such is used, the more likely it'll contain bugs and pose a security or privacy risk.
* People want more... what will it do next?
* Client side stuff can virtually always be bypassed in a generic way.

## To be fair

To be fair, there is one thing a client side checker can do.

Requirements:
* The software is hardly used by anyone.
* Your players can be tricked into using it.

Pro:
* Cheat consumers can't just download a random cheat client and use it on your server. Job done.

It could still happen that someone pays someone else (or is someone else) who then bypasses that client. In essence you probably don't really need a highly complex client side thing just for this use case, as nobody will even try to make a specialized client.

# Suggestions

Where could this possibly lead to?

## Future A: HACSS and HACCS

Hardware Anti Cheat!!

Think of a fancy piece of hardware needed to connect to your server. The suggested platform would cover an entire wall of a room and allow real-time streaming of everything inside the room to your server side interface (HACSS) or you subscribe to the cloud service (HACCS). Nothing your players could possibly do will go unnoticed, biometric data gathering will allow identifying real-life cheaters in a reliable way.

## Future B: PEACE BOTS

Since nobody is playing anymore anyway, just fake players by using 100% legit bots, also use bots for the remaining lot of actual players, use a fake server for the players to cheat there, and have additional 100% legit bots connect to the real server instead of the real players. Inform the players about their progress on the real server now and then. No more real-life trouble.

## Making Sense

If you want to confine your players to using a certain client, we suggest to do it right. Not sure this is right:
* Open source.
* No tricks, no exposing of additional data, no extra privacy violations, no legal trouble.
* Focus on sending extra packets to the server, with the design aim to erase false positives in the first place. This allows to make server side checks way more strict and removes a lot of server-side workarounds and special cases. Cheating gets harder, because the server expects the extra kinds of packets that just tell in more detail what the player is doing in-game.
* Of course cheating isn't gone that way, relax.
