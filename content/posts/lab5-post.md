---
title: "Lab Homework 5 : VR Locomotion Implementation"
date: 2021-02-28T15:56:58+01:00
draft: false
---
**Introduction**

My locomotion technique is based on the 3 dimensional maneuver gear from the famous manga named **Attack on Titan** (Shingeki no Kyojin). The main idea is to use two grappling hooks in order to be hooked to buildings or trees and then to move around them. 

Each grappling hook is controlled by one oculus quest controller (independantly from the other grappling hook). The player use raycasting in order to point to a surface. Then holding the index trigger allows the player to send the grappling hook to the surface he was pointing. While you hold this trigger your character is hooked to the same point in space. By holding the hand trigger, we reduce our distance to this point. It means that the rope which link the body of our character to the hooked point is shorter. The last interaction is to use gas evacuation. The player can click on the A button or the X button in order to evacuate gas. It allows the player to be accelerated in a direction. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/images.jpg" title="A character from the manga using gas evacuation" >}}

I learned a lot with this project because i was free (no slides to follow), I had to find my own way and I had to solve a lot of issues by myself. 

**Raycasting and LineRenderer** 

The first step was to implement raycasting. Thanks to the function named raycast in physics, raycasting is really easy to implement. But the main issue is that the user have no feedback when he is hooked to a surface. To solve this issue I found a particular component : the LineRenderer. It can render a line between two points in the space. Then the new issue is that the player is aware of where he is hooked when the grappling hook has been sent, but it's still really hard to send the grappling hook on a really precise area. To make it easier for the player I choose to add pointers. I just use a LineRenderer which shows to the player where he is currently pointing. During this step I encountered a last obstacle. Indeed, it's possible for an object to carry different component of the same type, but it's harder to select the good one in scripts. Here I need 4 different LineRenderers (pointer + rope for each hand). I thought that putting the 4 LineRenderers in the same object would be an important source of mistakes si I chose to create 4 new objects which will carry one LineRenderer each. It required a lot of organisation in order to make the code clean. The objects which carry the LineRenderer of the pointers have their own script which use Physics.Raycast(). The objects which carry the others LineRenderer will be used later and they are parameters of the Locomotion Technique script. So the raycast method here is called in the Locomotion Technique script. Later I had a last problem with the raycasting step. Indeed, it was possible to be hooked to coins or to the player collider. It's a big issue because sometimes it was impossible to send the grappling hook below our character's feet because the ray was hitting our collider first. The solution I found was to create new layers : "gameplay" layer and "not grappeable" layer. The "gameplay" layer includes coins and banners. The "not grappeable" layer includes all other objects which are only not grappeable such as the player collider. It's then possible to make the raycast function not hitting these objects. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155214166_1003694846703155_3858001085188543923_n.jpg" title="We can see the pointers for each controller and on one side we have a rope" >}}

**Gas Evacuation**

The next step was to implement the gas evacuation when the player push the A or X buttons. The idea is quite simple, the character has a rigidbody so we can apply force on it. So when the player push buttons, we apply a force on his rigidbody. The main problems in this part where about design. In which direction should we apply a force ? In the manga the gas seams to accelerate the characters in the direction their body is. So I tried to apply a force in the direction the player is looking to. It was quite good but there was an issue : we can't use gas to be accelerate in a direction while looking in another direction. And it's particularly a problem when the player want to be accelerated upward. So then I tried 2 distinct solutions : 
- pushing the A button to be accelerated in a direction which is a mix between the upward direction and the direction the player is looking to
- pushing the X button to be accelerated in the direction the player is looking to and pushing the A button to be accelerated in the upward direction

I chose the last solution because I thought it could give more control to the user and it could allows the player to reproduce easily the same movement from the original manga.

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/pb0.PNG" title="Some issues I had when implementing the physics of the ropes" >}}

**Some Physics ... :)**

The next step was the most difficult but also the most important. How could I simulate the grappling hook and the rope which link the body of the character to the hook. My first idea was to use a unity tool which already exists. I discovered really interesting tools : the joints. There are a lot of different kind of joints, the main idea of a joint is to simulate a link between two objects or points in space. I tried to use a spring joint between the character body and the point he is hooked to. But it was absolutely not what I wanted because even after modifying the parameters of the joint, I never succeded to simulate a kind of rope. And the problem with that is that with a high speed, the movement due to the spring joint are impossible to control (see right drawing above). Then I left this idea aside and try to find another way. I tried to apply forces on the character's rigidbody but I guess I was bad at physics because I didn't succed to set a right restoring force on the rigidbody. I dropped this idea. Then I tried to modify directly the speed or position of the character. The idea was to project the position of the character on a sphere centered on the hooked point and with the rope's length as radius. I dropped this idea because the update were not as fast as I thought so it was terrible, it was like a succesion of small teleportations (see the left drawing above).

Then I was locked because all the paths I imagined weren't good enough for me. But I remembered that there was a joint that I left aside : the configurable joint. With the right parameters we can simulate a rope. We have to make the 6 motion parameters as limited and we can adjust the size of the rope. It works pretty well. The last obstacle was that I needed 2 configurable joint since there are 2 grappling hooks. To do so I chose to create 2 objects which represent the hooks. They carry the Configurable Joint and also LineRenderers (see the *Raycasting and LineRenderer* section). 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155317399_900389147204422_5611194982152662947_n.jpg" title="The physics of the ropes work pretty well. Here I was hooked on 2 buildings" >}}

**Balancing Parameters**

The last obstacle was about being pulled by the rope using the trigger. I choose to apply a force in the direction of the hooked points to the character's rigidbody. I reduced the intensity of this force because sometimes the player was too attracted by the surface. But then there was inertia issues. To solve that I adjust 3 parameters : the mass of the character's rigidbody, the power of gas evacuation and the power of being pulled. It was quite hard and I'm still not convinced. It's hard because I had to do a lot of test to be precise enough on that. 

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/155226196_727269504645715_3060352108262427913_n.jpg" title="This city represents a city from *Attack on Titan*, that where the tests where more relevant" >}}

Finally I'm quite happy with the result, and some friends told me that it was really fun and cool. Moreover I'm happy and proud because I learned a pile of things about VR with Unity

{{< figure src="https://raw.githubusercontent.com/Wamzaa/HCIwebsite/master/static/img/2zkr4fuehxddafeee6juqk3pwxr72btd_00.jpg" title="I'm really happy with it" >}}
