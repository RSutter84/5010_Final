# Ralph's Final Project:

Link to final presentation video:
https://drive.google.com/file/d/1eROqGxeXjnD3qMpPrfRbTWMIAlbyvYxh/view?usp=sharing 

For my final project, I wanted to explore using HLSL code predominently for shader work in conjunction with Unreal Engine. I ended up also using it with a Niagara particle effect.

## Niagara Particle System - HLSL Spawn Component
My first step was actually the latter, I've always struggled with Niagara - in particular with getting organic results when it comes to how particles spawn. So I ended using scratch pad in my Niagara system to control how particles were being spawned.
![Screenshot 2025-06-04 152406](https://github.com/user-attachments/assets/c98be399-6013-42e1-bbd4-9f85263a2aed)
In a nutshell, particle systems generate a unique particle ID for each new particle that spawns. Using this component, I could tap into that data set to generate variations in how each unique particle was then generated. Which yielded a really interesting pattern with much less random tinkering than by going through all of the sub-menus within a Niagara system.

## Raymarching Shader
My second goal was to create a raymarching shader in Unreal. I know I had initially toyed around (pun intended) with the idea of using ShaderToy to create a shader, and then converting the GLSL to HLSL so I could use it in Unreal. But it didn't seem very efficient. So I ended up just using Unreal directly for it. 

I started off by making a shader that had a custom node assigned to the albed/color slot. This custom node allows you to use HLSL directly within the shader graph. In terms of my code, I kept things very simple and used a base 1 x 1 grid texture as my input/color component. With most of my code focusing on the manipulation of the UVs themselves and some conditional color tinting. 
![Screenshot 2025-06-04 152341](https://github.com/user-attachments/assets/91481304-0a45-4749-93c3-c5f6ae9bbb2a)
Even though it is relatively simple, it took me quite a bit of time to get it to work because of my sloppy syntax :) Also, whenever you are in the middle of coding and save, sometimes Unreal will crash because it (naturally) tries to then execute the code. So I ended up writing my code in Visual Studio after it happened a second time.

## Supplementing the shader work with Blueprints and sound envelopes
I wanted to have most of the components of my shader react to audio. The way I approached it was by importing my audio track and enabling audio envelopes (which is a really simplified way for Unreal to detect certain sound ranges. With that set up, I then created several scalar parameter values in my raymarching shader. Using a Blueprint and a Dynamic Material Instance, I could then expose those parameters to the values read from the envelopes.
![Screenshot 2025-06-04 153928](https://github.com/user-attachments/assets/26636409-2eb3-49ed-8cb6-cfb6c5d6a714)
So the envelope data basically drives the majority of the scalar values after the HLSL code has run its operations.

## Conclusion
I learned a lot! Not just with this project, but the semester in general. Code has always been daunting to me, but I really feel eager to experiment with it more. I am also really happy that I took a dive into seeing how you can combine code with Blueprints in Unreal. I feel like a whole new world is opening up to me and I am excited to see how it will transform my work! 
