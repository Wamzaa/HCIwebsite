---
title: "Lab homework 3 : Unity Roll-A-Ball"
date: 2021-02-28T15:56:17+01:00
draft: false
---

In the Roll-a-ball tutorial i didn't really had difficulties because the tutorial is pretty well explained. But I learned many usefull things about Unity. The goal of this project is to create a game in which the player controls a ball in a closed field thanks to the directionnal arrows. The ball have to hit cubes in order to collect them and increase the player's score. 

First I learned the main component of a scene : the GameObjects, the lights, the materials, etc... . Then I learned how to play with the physic of a GameObject by using his rigidbody and applying forces on it. We also learned one of the most important component of a Unity project : the script. A script is a code with parameters, in which some functions are called when an event occur. So here we just create a script to apply forces on the ball when input events occur. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/rollaball.PNG" title="Classic Roll-a-Ball game" >}}

In the next part we create a new script to make the camera moving with the ball. And here I discovered another important element : the Transform component, it contains the position, rotation and scale of an object. We manipulate this component in scripts and it's really powerfull because it give a lot of controll on GameObjects. Later I discovered the prefabs, it allows to create several similar objects and modify all of them at the same time. Then I learned how to manage collision by using the OnTriggerEnter() function and by using some parameters such as IsTrigger, isKinematic or UseGravity. When a GameObject with IsTrigger collides with a GameObject with the function OnTriggerEnter() in a script, this function is called. An object with IsKinematic is independant of forces. Then I learned how to display text. I understood a lot of Unity basics in this tutorial 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155294258_231413462019350_7422850396374829071_n.jpg" title="Roll-a-Ball in VR" >}}

Then the next step was to adapt this game in VR. I didn't encounter too much obstacles since everything was explained in the slides. We first have to create a new project and import the package of Oculus Integration, and then import a package which contains the elements of our classic roll-a-ball game. I learned how to use the input from the Oculus controllers. In this example we just have to check the value of the trigger. Eventually I learned about the layers. It was the hardest part of this lab because I spend a long time time to understand. The main idea is that elements from distinct layers can't interact together. So here, the ball, the walls and the collectibles aren't on the same layer as the collider of the board and the controllers. This lab was quite interesting because I realised that it's not that hard to create a VR game

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155143688_184512296442235_201895343635526591_n.jpg" title="Roll-a-Ball in VR : moving the board" >}}