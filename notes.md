---
title: Viva Notes
---

# 1 - Intro
Welcome to my viva presentation for my EG-353 project, "Low-cost telemetry payload for high altitude balloon"

# 2 - Presentation Outline
I'm going to start with a brief background into high altitude ballooning, followed by my research objectives. I'll then discuss my methodology and the results gained from my tests. Finally I will discuss those results and show my conclusions

# 3 - History of High-Altitude Balloon launches
High Altitude Balloons have been used since the turn of the 20th century, primarilly for taking airborne meteorological measurements used to create weather forcasts. High altitude balloons are also used for a variety of science experiemnts, from gamma ray astronomy to ozone measurement. Manned hot air balloons were originally used for this purpose, but were shortly proceeded by unmanned helium balloons, which are still used to this today. Currently 1,800 high altitude balloons are released worldwide every day.

# 4 - High Altitude Balloon Launch Procedure
The flight procedure of one of these balloons is as follows: the balloon is filled with a precise amount of lighter than air gas such as helium. When the balloon is released, it rises at about 5 meters per second, taking measurements and transmitting telemetry. As the latex balloon increases in altittude, the differential in inside to outside air pressure causes the balloon to expand. Once an altitude of roughly 30 km is reached, the balloon bursts and the payload falls to the ground. A small parachute is used to slow the descent rate to a safe value. When the payload lands it's radio signal is used to for locating it.

# 5 - Problem with the Current Commercial Method
There are commercial offerings available; a common example being the Vaisala RS41 Radiosonde. These cost about £100 each and consist of ready to deploy sensor and tracker modules. Devices such as these are usually only available to industrial customers in high volumes.

# 6 - Solution
The solution I'm proposing with my project is to design a low-cost payload that is built from readily available consumer parts such as hobbyist microcontrollers, off-the-shelf sensor modules and consumer available batteries.

# 7 - Objectives
The objectives I set myself ways to create a low-cost microcontroller based payload, integrated digital multifunction sensors, minimise weight in order to reduce launch cost and to reliably transmit telemetry over a 30 km distance.

# 8 - Project Background - RTTY
For some background information I will explain the operation of the RTTY mode. Radioteletype uses frequency shift keying to transmit data over radio. FSK transmits binary data by switching between two carrier frequencies. it's very resilient against the Doppler effect which is something that must be dealt with as the balloon crosses the horizon .

# 9 - Project Background - Link Budget
Link budget equations are used to calculate the performance of a theoretical radio link by taking into account all of the gains and losses in the system. My calculations showed the link margin to be 11dB, which indicates that good performance will be achieved at a range of 30km.

# 10 - Methodology
In the next section I will discuss the overall system design and components used, as well as showing the software design. I will talk about the antenna design and demonstrate the ground station setup. Finally, I will talk about the testing methodology.

# 11 - Overall System Design
Shown is an overall block diagram of the payload, showing the main components and how they communicate with each other. I squared C is used to communicate with the sensor modules, and the NMEA protocol to communicate with the GPS module.

# 12 - Circuit Diagram
Next is the circuit diagram that was designed in kicad. This shows how the payload components are electrically connected to each other, and what passive components are needed to support them.

# 13 - Construction Methods
A CAD design was used to lay out the parts. In the picture you can see the battery pack and main microctroller module inside the enclosure, as well as the external sensor and GPS modules. These parts are all housed inside a polystyrene enclosure for shock resistance and insulation.

# 14 - Programming
Now I am going to show you some key aspects of the code. *Switch to code*. The code was written in Arduino C. 

The first part I'd like to draw your attention to is the setting of GPS flight mode. Ordinarily GPS modules such as the one I'm using are designed to disable themselves if they detect use at a high altitude or high speed, to prevent them from being used in military applications. A data string is sent to the GPS to disable this flight mode, and a confirmation is given by the GPS when this has completed successfully.

*CRT + ALT + L*
This next section runs in a continuous loop. The GPS and sensors are polled for their latest information, and the data is parsed into a format that can be sent over the radio. A UK High Altitude Society telemetry is string is used to ensure interoperability with online systems. Finally, a checksum is calcualted to allow the receiver to detect eronious data

*CRT + ALT + L*
The final section is used to break the transmission string into individual characters that can be sent to the radio module. FSK modulation is achieved by setting one of the Arduino's pin either high or low depending on the bit of information being transmitted.

*Back to the powerpoint*

# 15 - Antenna Design
The next section of the project was to design the antennas. 2 main different types we used, a directional Yagi antenna and an Omnidirectional quarter wave groundplane antenna. Both designs were validated in the 4nec2 antenna modelling program, which produced these 3D gain plots. You can see the major lobe in the Yagi in this image

# 16 - Antenna Design
and this image shows how the groundplane antenna radiates mostly upwards

# 17 - Ground Station Setup - Live Demo
*Switch to demo*
I'm now going to do a live demo of the payload functioning. I'll first connect the power cable to boot the Arduino and start transmission. *Switch to SDR#* You can now see the SDR sharp program which is communicating with an SDR reciever to demodulate the signal. The audio from SDR sharp is sent to DL fldg which is the risky decoding software I used. *Switch to DL-FLDIGI* You can hear the audio of the RTTY signal and also see the the signal being decoded in real time in the dl fldi.

# 18 - Testing Methodology
So next we will talk about the testing methodology I ran a number of tests the first which was a cold temperature durability test I needed to validate the payload work at cold temperatures so I put it in the freezer downstairs for two hours it's about minus 20 degrees Celsius monitoring the radio transmissions throughout. I also weighed the payload, did mechanical shock test by dropping it from high to five metres and  a battery life test running the payload with a fresh set of batteries until it's stopped working. Finally I performed a test of the radio transmitter i did this by performing multiple signal to noise measurements at different distances away from the transmitter.

# 19 - Final System Design
The final system design is now shown. You can see how the components are laid out in the polystyrene enclosure; including the two external components

# 20 - Results
The first of my results was a graph of the freezer temperature. You can see the test was run over 2 hours and there's no anomalies in the data. The readings were shown to be accurate and reliable. 

# 21 - Results
Here is the signal to noise ratio graph for the radio test that you can see the distance which that was used for the test. This data could have been improved by using calibrated test equipment such as a vector network analyser.

# 22 - Conclusion
The tests showed that the payload design could be a viable replacement solution to commercial offerings, at a much lower price point. The testing could be improved using calibrated laboratry equipment which would better characterise the performance of the payload

# 23 - Discussion
Some future improvements this product I'd like to design a custom printed circuit board provides better mechanical connexion between the components as well as using some locking connectors which are less likely to come loose on landing. These limitations were due to the COVID-19 pandemic reducing access to Swansea University's lab equipment.

I'd like to thank my supervisor Dr.Davies and the Swansea Radio Society for providing funding for this project. Thank you for listening.


