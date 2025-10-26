---
title: Raspberry Pi Radio
date: 2025-10-23
cover:
    image: "/images/projects/tinkeringcover.png" 
    alt: "Tinkering"
    caption: "My Custom Moode Radio"
    hidden: false
summary: "Building an Internet Radio to fill the void"
author: Andrew Cambron
---
## The Problem
Where I live in Delaware is often nicknamed, "Radio Free Newark" for it's lack of terrestrial broadcasting. Too far from Philly to consistently pick up WHYY or WXPN: our household was feeling the pain.

### Constraints
1. Cheap as possible. I had already picked up a [Sangean HDR-19](https://www.amazon.com/dp/B0CQB39KM1/?smid=A3SBDOAENTRT1F&tag=thewire06-20&th=1) for a pretty penny.
2. I wanted to find something that could quickly and affordably add Internet Radio using the Sangean's existing AUX in.
3. Had to connect to the internet over WiFi
4. A screen to display the station ID.
5. A power button and a tactile way to change the station

## Process
* Knowing next to nothing about the task I set to embark on, I sought out software to help me with my goal. 
* After trying out Volumio, I eventually settled on Moode for my project. I liked their (at least for now) commitment to open source principles.
* I quickly felt that trying to repurpose my old Raspberry Pi Model B was a fools errand, and upgraded to a Pi 3 with onboard WiFi and Bluetooth. (I may have come to regret that, but more later.)

### Beta Testing
1. Running the software on a stock Raspberry Pi turned out ok. I could successfully play stations, and show my wife how to change stations.
2. Biggest downside was needing to use a web app to control the radio. I wanted something tactile, and device-free.
3. Dire need for a case due to Kitchen use.

### 3D Printing
1. As this was the step I was least comfortable with, I started working out the design before I finished the custom scripts or electronics.
2. Having never 3D printed anything, I gave myself a crash course in using Fusion 360 and an Ender 3 printer.
2. After some basics tests, I set out on what would be the most challenging part of the process: designing a snap in plate for a [16x2 character LCD](https://www.adafruit.com/product/181?srsltid=AfmBOorQGaDkA9XH-GFX-4y5j-6KY1b1wJDZVoCpUn7ct2_PiIU5XjiS).
My initial design concept was to apply what I had learned building Eurorack synths, and create a modular way to add one of these LCDs to a regular sheet of project panel (1.6mm thickness). While ultimately an unnecessary step for this particular project, I think it could be of use to other makers down the road.
3. I ended up deciding to build a small enclosure that would fit on top of the Sangean, while mirroring some of the Mid-Century revival style choices.
4. In the end, I opted to 3d print the 1.6mm panels (due to lack of access to a Dremel or drill press)

{{< figure src="/images/tinkering/isometricdrawing.png" title="My CAD model" caption="Always wanted to make one of these cool exploded views... so I learned how to do that too." width="100%" >}}


### Electronics
1. In my initial plan for this project, I had envisioned using a potentiometer to dial in the station; attempting to mimic an analog car stereo.
2. I breadboarded out some of these ideas, using repos I found on Github to try to reproduce their functionality. Ultimately, I would end up having to roll my own due to issues I was encountering with version mismatch.
3. After successfully breadboarding the project (or at least breadboarding about 85% of what I had hoped to accomplish) I set to wire up the radio using a [ProtoPi Hat](https://www.adafruit.com/product/2310?srsltid=AfmBOopk3Hw4p4njpvL5NEcT4WfUobF4QNOaEhK0hfrEW1BVKBm3WJaa) if by some miracle this worked, I wanted to potentially ship these off to PCBWay to make them as a Christmas Gift.

### GPIOs, Vibe-Coding, Python experiments and more.
1. While I have run through Linux tutorials and used Homebrew to run scripts I do not fully understand; I had never before tried to freewheel through any kind of coding/scripting task from scratch.
2. I had hoped, naively, that I would be able to find and use existing repos to make my project work, without having to get my hands dirty.
3. Unfortunately, my limited CompSci know-how meant that I would spend days stumbling over version mis-matches and kernal panics before I attempted to vibe-code my way to glory.
4. Initially, I had intended to use Gemini to debug my code, (As I had done with some other scripting issues I had flare up in the past.) but by the end of the process, I was fully letting LLM Jesus take the wheel.
5. I would finally end up with a version of Moode, running a custom script to display the station information. 
{{< figure src="/images/tinkering/radio.png" title="The finished product" caption="Ready to stream my buddies on WFHB" width="75%" >}}

## Next Steps
1. I think at this point, I can say that V1 of the radio is done. 
2. I would like to revise the design to use the default GPIO button mapping for Moode. Custom interface design has not proved to be worth the time and energy required.
3. I would like to take the code to someone who better understands Python. I suspect the code has a memory leak, as the radio becomes slower to interact, the longer it is left on.
4. I would like to redesign the case to have a removable sled for the Raspberry Pi. During debug, it can be very frustrating to remove and reinsert the pi. A little more time on that would make me happy
5. Move control buttons to the top of the radio, and leave the face panel dedicated for the display and power.

## Documentation
1. [Moode Software](https://moodeaudio.org/)
2. [Custom Python Script to Drive Display](https://github.com/ajcambron/moode-lcd-display-gpio)
3. [16x2 Faceplate on Thingiverse] -Coming Soon
4. [Radio Enclosure on Thingiverse] -Coming Soon


