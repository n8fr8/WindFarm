#StatusCasting Overview

Status Casting (or just statcast or maybe even just “scast!”) is the name I am giving to the act of using the built-in radio broadcasting capabilities of your mobile device, laptop, wifi router or other radio-enabled device to broadcast a short human-readable message up to 10m to 100m away. I’ve been exploring this concept for the past few weeks on this site.

Rather than naming your Bluetooth device “Nathan’s iPad Mini 2″ or “Joe’s Nexus 6″, you would rename it “!Please send coffee to 10 Main Street” or “#elections vote for Mr. Big” or “@dictator you are a real jerk!” or perhaps just “What a beautiful day :)”. Instead of naming your wireless network “Netgear Guest Network” rename it “Hot Cocoa at Joe’s #snowpocalypse” and bring your neighbors some cheer! While each message may only be seen by people within 10 to 100m away, those people can then modify their message to repeat and reshare what you have written, or vice-versa. In this way, the effective distance your message might travel is quite far. This is not unlike how a Twitter status update “travels” – it might get lost and seen by no one, or it might catch someones eye, who retweets it to their 100,000 followers. You never know!

As the example messages above show, this could be used in a variety of situations, in the aftermath of an earthquake or hurricane, to critical “get out the vote” days in a political campaigns. It is useful in geographies where speech is restricted, or just to express how you are feeling to the humans in your immediate area, well in fact, up to 100 meters away in some cases, which is quite a lot of people potentially.

While the system has no built-in notion of “full name” and no real name requirement, some might consider it anonymous, in a sense. However, any miscreant looking to abuse this system does have to be physically present in the area, and all messages are ultimately tied to a hardware device MAC address on a Bluetooth or Wifi radio. This is both a benefit and a risk of course, and more threat modeling and countermeasure planning needs to be done, to both considering the impact on bad actors and users.

The concept of status casting can be uses without any extra apps or software. However, through an app, you can build a more pleasing, usable experience on top of this concept, and that is what Gilga is: https://github.com/n8fr8/gilgamesh

#Repeat vs Retweet

There are two behaviors I have been considering during my adventures in human-powered mobile mesh these last few weeks. The first is Retweet or Reshare, as invented by Twitter users manually (“RT @foo this is important”) and then later on built directly into the Twitter platform as a feature. The second is “Repeat”, as inspired by radio repeaters.

Retweet (RT) is meant as a human-powered endorsement of a message. The meaning and content of the messages have been ideally verified, or at least the source is trusted.

Repeat (RPT) is meant to allow a message to extend further in its reach, by allowing the receives device to reshare it another 10 to 100 meters from its current and future positions. It is an active way to participate in extending the mesh, but it should not be seen as endorsement of fact or an act of verification or trust.

A mixture of retweeters and repeaters in a crowd, can then extend the reach of a message from 10m or 100m up to say, 400m in the drawing below. A repeater might be a fixed device, say a phone or tablet with a good solid antenna plugged into a battery pack or an outlet somewhere.

!(img/StatusCasting-Diagram1-1024x717.png)

A retweeter is more likely a person in the crowd, moving through the area in a variety of directions. As they continue moving however, they will keep rebroadcasting their last few tweets, including the retweet. As they encounter new receivers / lurkers, they will receive the original message, and the mesh is now extended in a non contiguous-manner.

!(img/StatusCasting-Diagram2-1024x717.png)

The Gilgamesh app supports a simple two-tap feature to manually reshare any status message you have received. Once this is done, your device then rebroadcasts the message over its Bluetooth and Wifi radios, with the expected “RT @900734 i am live on air” format. Also, remember beyond this particular app, any user can manually set their Bluetooth device name, be it a laptop or an iPad, to use a similar format. The app also now supports an automatic repeater mode, that can be easily toggled off and on. In this mode, *ANY* message you receive is automatically rebroadcast, using the “RPT @900734 does the repeater hear me” syntax. You can see this in the screenshot below.
device-2014-10-06-165429  device-2014-10-09-120044

Ultimately, because we are limiting this experiment to a very simple plaintext status messaging system, we have made our lives very easy, and made the possibilities of successful use quite good. Since we aren’t concerned with routing internet protocol or creating a reliable LAN network that can sustain HTTP, we can take advantage of ideas like non-contiguous meshes, retweeting and repeating to extend the range, reach and impact of the communications.

In the screenshot, you might have also seen the use of direct messages with delivery confirmations. I will cover that in a future post, as it is another complex and fascinating topic of possibilities!

#Dynamic Bluetooth Names on Linux

First committed here: https://github.com/n8fr8/gilgamesh/blob/master/docs/linux-howto.txt

Since the Gilgamesh system uses plaintext bluetooth names for its basic broadcasting communication mode, it is a very easy system to participate in from any desktop system. Below is the set of steps that can be performed at the Linux command line to configure the device name to be up to a 248 byte message (~248 ASCII characters, or ~60 Unicode characters).

These commands can be easily used to build a stationary repeater system, using a high powered bluetooth antenna, or you can just use them to broadcast your own status constantly in the background, to anyone in the area who might be listening.

1) Install Bluez Tools (https://code.google.com/p/bluez-tools/)

> sudo apt-get install bluez-tools

2) Find your Bluetooth adapter

> sudo bt-adapter -l

Available adapters:
default-device-name (A1:B1:C1:D1:E1:F1)

3) Set Discoverable and Powered

> sudo bt-adapter –adapter=A1:B1:C1:D1:E1:F1 –set Powered true
> sudo bt-adapter –adapter=A1:B1:C1:D1:E1:F1 –set Discoverable true
> sudo bt-adapter –adapter=A1:B1:C1:D1:E1:F1 –set DiscoverableTimeout 3600

4) Change the name of your device to a Gilgamesh compatible string (starts with space or special character)

> sudo bt-adapter –adapter=A1:B1:C1:D1:E1:F1 –set Name ” this is my laptop it is a great big BT device”

5) Listen for and discover other devices in the area

> sudo bt-adapter -d

Searching…

[A2:B2:C2:D2:E2:F2]
Name: Now what. This is a message from my phone…yo..
Alias: Now what. This is a message from my phone…yo..
Address: A2:B2:C2:D2:E2:F2
Icon: phone
Class: 0x5a020c
LegacyPairing: 0
Paired: 0
RSSI: -59

Update: Added bash script to make it simpler:https://github.com/n8fr8/gilgamesh/blob/master/docs/gilgamesh.sh

> ./gilgamesh.sh
> Powered: 1 -> 1
> Discoverable: 1 -> 1
> DiscoverableTimeout: 3600 -> 3600
> What’s happening nearby? this is a big ol’ test
> Name: this is a really long string that I am typing now!!!! -> this is a big ol’ test
> checking for local updates…
> Searching…
