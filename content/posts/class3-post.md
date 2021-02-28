---
title: "Class Homework 3: Sketch and present 3 ideas for Locomotion in VR"
date: 2021-02-28T15:56:25+01:00
draft: false
---
**3D Maneuver Gear**

My first locomotion technique is based on the three dimensional maneuver gear from the famous manga named Attack on Titan (Shingeki no Kyojin). In the manga the characters are using grappling hooks to move around buildings or trees. Each character has one controller in each hand, a gas tank and a grappling hook launcher on each side, and a gas evacuation system in the back. Thanks to the controllers they can send a grappling hook on a surface, pull back the grappling hook, pull on the rope fixed to the grappling hook in order to be closer to the surface they are hooked to. When a character is hooked to a surface, he is only able to move inside a sphere centered on the hooked point and with the rope's length as radius. Moreover the characters are able to evacuate gas in their backs in order to move faster in a chosen direction, it allows them to be more flexible in their movements.

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/db0a67bab642f3780a33c421abf5f3c4.jpg" title="The 3D maneuver gear from **Attack on Titan**" >}}

The metaphor with the Oculus Quest is quite easy to understand. Indeed, the player use two Oculus controllers which represent the three dimensional maneuver gear controllers. We can use raycasting to point a surface in order to send the grappling hook, if we push the index trigger we send the grappling hook and while we hold this trigger, the grappling hook stay hooked. We can push the hand trigger to be pulled by the rope. The two controllers are independant. Eventually the A and X buttons will allows the gas evacuation. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/loco1.PNG" title="Short description of the metaphor" >}}

This Locomotion technique is the one I've chosen to implement. In this locomotion technique, I want to evaluate how fun it is and how much the fans of the Attack of Titan are happy to control the famous maneuver gear they probably dreamt of. Of course, I could also evaluate the motion sickness and how much precise this locomotion technique is, but I think that the fun and the similarities with the original manga is more important since this locomotion technique is fan-based. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155214166_1003694846703155_3858001085188543923_n.jpg" title="Aspect of my locomotion technique (implemented)" >}}


**Rabbit Jump**

My second locomotion technique is the rabbit jump. The idea is to move thanks to consecutive jumps. I'll just explain how to make one jump, to make more complex movement the player will just have to make distinct successive jumps. To jump the player have to choose a direction by pointing with one controller, the user don't have to point on a precise point in space, only the orientation of the controller is important. Then, you have to hold the index trigger and release it. The longer you hold the trigger, the more your jump will be powerful, and when you release the trigger, you will jump. I think that it's not really tricky to implement. I think that just adding a force on the character's rigidbody during less than 1 second would be enough to jump. Then, to give feedback about the current power of the jump before releasing the trigger, a kind of jauge could be add near the virtual hand of the player. Eventually, some work should be done to make the player landing correctly on the floor instead of continuing moving, or rolling. The two important parameters are the orientation of the controller and the power of the jump. The jump will be done with the power selected in the same orientation as the controler. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/loco3.PNG" title="Short description of the metaphor" >}}

The goal of this locomotion technique is to have a kind of smooth teleportation : you can't move freely on the ground, you are only in contact with discrete point on the ground (like a teleportation), but it's not really a teleportation because you have a real trajectory. The others goals are to be a fun locomotion technique, it can be calm and precise with enough training, and eventually it could help the storytelling (the story of a rabbit, of a cosmonaut on the moon, of a frog, ...). To evaluate this technique we could measure the amount of fun, the precision, the speed and the motion sickness. I think that this technique could be used to be really fast, or really precise, or can be use to move calmly and prevent motion sickness, it depend of the way people use it.

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/0b2878a60e1e125cf73f95bcec58f7c0.jpg" title="A VR game could tell the story of this rabbit ... " >}}

**Motorbike**

My last locomotion technique is the motorbike. The idea is to simulate a virtual motorbike and drive it. The user have to place is hand like if he was holding handlebars. Then the tilt between the two controllers is computed and used to make the motorbike going on the left or the right. The right trigger allows to adjust the speed, and the left trigger allows to control the speed when going backward. I think it's not too hard to implement : we can control the Transform of a GameObject thanks to all the inputs the way I just explained before. And then we have to link the player rigidbody to this Gameobject. I don't know if it's necessary to make the player's camera moving with the motorbike but I think so because otherwise the player would have to turn around himself all the time. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/loco2.PNG" title="Short description of the metaphor" >}}

The goal of this locomotion technique is to be fun and feel the sensation of speed : feel like being on a true motorbike but without the dangers. So the goal is a high presence. To evaluate this locomotion technique we could evaluate, the feel of speed, the fun, the precision and the presence. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/excited-biker-with-a-vr-headset-pretending-to-drive-a-motorcycle-picture-id859654256.jpg" title="A player driving a virtual motorbike" >}}
