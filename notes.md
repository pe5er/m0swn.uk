---
title: Viva Notes
---


Welcome - Hello I’m Peter 

Presentation outline - start with brief background on the project followed by x, y, z

History of HAB- What are they used for purpose and usage overtime 
•	Meteorological experiments - measuring temperature and pressure - to predict changes in weather over, air sampling gamma ray astronomy and ozone measurements amongst other things.
•	These measurements in the oast - taken by hot air balloons then kites but helium balloons were developed in the 19 00’s - latex balloons filled with helium - lighter than air.
Next Slide
•	Flight path of one of these balloons- procedure is; to set up ground station fill ballon with helium, checking amounts of helium to weighing it - when it can lift a bucket or is neutrally buoyant it is full, then you’re ready to attach the payload and launch
•	Rises 5m/s , rises fairly quickly to up to about 30km at which point the ballon goes up in altitude and the outside airpressure decreases - internal pressure constant- balloon expands - at a certain point (predicted using ballon information) ballo bursts and payload falls to earth. Payload is attached to a parachute - which used to slow the descent to a safe value in order to prevent damage to the payload or other objects as it lands.

What's the payload lands we use the radio signal from payloads in order to locate the payload although certain meteorological flights don't recover the pillows and they they they lose it effectively what the mess office do with their launches but for a kind of scientific experiment like for the one I am conducting intend to recover the payload myself using the GPS 

So there are commercial offerings Mabel hear a common ground this is radio songs you can buy companies by radius Arms at about £100 each and these are ready-made trackers and sensor devices that can be attached to balloon and sent off and quite expensive and usually only available to industry customers and also sold in high volumes Met Office launch 600 balloons I have no idea if I can get us sister quite eventually So the solution I'm proposing with my project is desire low-cost payload that spilt from readily available consumer parts such as hobbyist microcontrollers off-the-shelf sensor modules and consumer available batteries 

The objectives I set myself ways to create a low-cost microcontroller based payload integrated digital multifunction sensors and weights in order to reduce launch cost at to reliably transmit celebrity over 30 km in length 

Just the background to tell if information there's a couple of things I'll be talking about one of them is pretty radio tele type this is based off frequency shift key modulation which is a way of transmitting binary data by switching between two carrier frequencies it's very resilient against the Doppler effect which is something you have to deal with the balloon music cross the horizon 

The other thing we will talk about is a link but this is some maths we can do in order to figure out whether the proposed radio system is able to transmit over the distance you need it to and we do that by taking into account all of the games and losses in the system in order to calculate the power that will be received by the ground station 

I'm so now I move on to the method section we're going to talk about the overall system design the components used I'll show you the circuit diagram I built to be talking about how the software was developed and it also the antenna side of things 

The festival I've got a overall block diagram for you this 2 shows the major components used in the payload and how they communicate with each other 

Next you got the circuit diagram at this was designed in kicad and shows how the payload is Bill's electrically and how the modules are connected to each other 

Go to How can I do a quick Through of the code with you 

So the code is written in Arduino see at the top here we include the libraries we're going to use for GPS and the sensor module and then we start by assessing up the pass the code they need to run on startup but to only once so this is things like setting up the GPS an the sensor an the radio and telling you know which pins needs to use to communicate with which devices next thing we do is we initialise the GPS something important that has to be done here and that's setting GPS into flight mode ordinarily GPS modules such as well I'm using designed to disable themselves if they detect use at a very high altitude an over high speed this is just open from being used in military applications so this bit of code here sends a set of data gps module that puts it into flight mode right OK so now we move to the part of the code that runs continuously the first part of this poles the GPS and the sensors in order to get all the data that we want for this for this cycle and following that we convert all that data into the format we want to send it over the telemetry link and that's done in this printf statement here and then finally we we assemble that data for the radio to send over the Cemetery link and this is done down here I think then get sent over radio once that's completed the code just runs continually and it ends up doing a a whole cycle about once every 10 of 20 seconds 

So the next section of the project was to design the antennas that were going to be used 2 main different types we used directional Yankee antenna and an Omni directional quarter wave groundplane antenna these were well the yaki was designed from a like a look up table and the ground plant endo was just designed from basic principles both designs were validated in the four NE C2 and telling modelling software which produced these 3D gain pattern plots as well as 

\so now I'm going to do a live demo of the pair functioning itself so first thing we do is I'm going to plug it into the power so that it starts transmitting and then I'm going to show you how the software receiving chain works amazing and rcl SDR dongle as a SDR receiver and the stl sharp programme communicates with that dongle and shows me a section of radio spectrum I locate the signal in the spectrum and the audio from this programme is then sent to DL fldg which is the risky decoding software I used for my product you can hear the audio of the ressie and you can also see the the signal being decoded in real time showing up in the dl fldg 

So next we will talk about the testing methodology I ran a number of tests the first which was a cold temperature durability test I needed to validate the payload work at cold temperatures so I put it in the freezer downstairs for two hours it's about minus 20 degrees Celsius monitoring the radio transmissions throughout that. I also did mechanical shock test by dropping it from high to five metres I repeated that a few times uh and also a battery life test running the payload with a fresh set of batteries until it's stopped working simply weighed on the scales as well and finally performed a test of the radio transmitter i did this by performing multiple signal to noise measurements at different distances away from the transmitter which 

So the final system design is now on the screen you can see the policy I mean housing that's used to insulate the payload the battery pack on the bottom right with a low drop out three point 3 Volt regulator for the Arduino on the bottom left you can see the GPS module with the antenna exturnal to the enclosure so it gets a good signal and at the top left you can see where the telemetry antenna exits the box and where the multifunction sensor also exits the box top middle is the seca boredom 

so onto results the first thing i got here is a graph of the freezer temperature you can see the test is run over 2 hours and there's no anomalies in the data at all could show see accurate and repeatable readings 

and here is the signal to noise ratio graph for the radio test that you can see the distance which that was performed on the 

So yeah my computer I rate the payload as a viable replacement solution to commercial offerings there were i 

Some future improvements this product I'd like to design a custom printed circuit board provides better mechanical connexion between the components as well as using some locking connectors which are less likely to come loose on landing I've also changed parts of the methodology it would be good to use calibrated test equipment to measure the radio performance as well as doing a cold temperature test as a temperature more akin to what the payload will be subjected to in flight and there were these were mostly limitations due to cover 19 and having reduced access to swansea 

