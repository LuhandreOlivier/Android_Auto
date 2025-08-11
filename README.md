# Android_Auto
Using a raspberry pi 3 to add android auto to my 2012 Toyota Auris.

Table of Contents
Project Description

Problem Statement

Technical Stack & Justification

Key Features

Challenges & Learnings

Installation & Setup

Usage

Future Enhancements

Acknowledgements

Project Description
I am passionate about cars and I believe all cars have a soul and the more you personalize a car the more soul it gains. You are giving it a story to tell.
This is why I love older cars since their stories already have so many chapters, but modern cars have many comforts older cars don't have like android auto and
even headlights that power off automatically. That is why I have decided to tackle some of these issues on my 2012 Toyota Auris.

The idea is to use the opensource crankshaft software and pair it with a raspberry pi 3 model B and a 7 inch touchscreen display. This will allow me to connect my phone to the
raspberry pi and the crankshaft software will then boot into android auto.

Problem Statement
This is where you show your critical thinking. Why did you build this? What problem were you trying to solve?

With the standard head unit of my car there is a lot of information that I cannot see such as music information like what song is playing, as well as navigation information
when traveling to a new destination. The standard head unit is also very unintuitive making it difficult for other people to connect to the radio if they would want to play music.

Technical Stack & Justification
The components I will be using for this project are:
- Raspberry pi 3 model B
- Hosyond 7 inch touch screen display, 800x480 resolution
- 5V 3A buck converter
- 12V relay
- Miscellaneous components eg. Diodes, Capacitors, Wire, Protoboards, BJT's etc.

Most of the heavy lifting has already been done since crankshaft handles the phone connection and displays android auto. There are two main hurdles. Sound and shutdown.
I will not be going into detail into the sound issue since that was solved with mainstream components and will be discussed later. The shutdown problem is however important.
The issue with the raspberry pi is that you cannont just remove power from the pi since this could degrade components over time like the SD card reader, the SD card itself etc. 
To circumvent this we need the pi to excecute a shutdown command when the car is turned off and it needs to be powered for long enough so that it has time to excecute the command
which takes about 10 to 20 seconds. That is what the miscellaneous components will be used for. We will build a circuit and write a script that allow the raspberry pi to monitor a
GPIO pin that will change state when the car shuts off and we will build a circuit that will supply the Raspberry pi with power for about 30 seconds after the car has shut off just 
for incase.

Software:

The two potential options when trying to run android auto on a raspberry pi, Crankshaft NG or OpenAuto. The first thing to note is that Crankshaft is based on the OpenAuto core software
and is designed to be a "turnkey" solution whereas OpenAuto is an application that you will install on the standard Raspberry Pi OS. OpenAuto has two different variants,
OpenAuto Pro and the normal OpenAuto software. OpenAuto Pro includes many features more that standard OpenAuto and Crankshaft. I chose Crankshaft not only due to it's ease of use,
but also because OpenAuto and OpenAuto Pro is designed to run on a newer Raspberry Pi 4 and I will be using the Raspberry Pi 3 model B.

Hardware:

The biggest choice in this project is the Raspberry Pi. I chose the model 3 B quite simply because it is what I have on hand and because this project can get very costly very quickly,
therefor having proof of concept is very important before spending the money on a newer Raspberry Pi and different software. It is also worth noting that it will be very easy to upgrade
the project in the future since all of the components around the Raspberry Pi will not need to change as the screen is also compatible with the Raspberry Pi 4 and power will also not
be an issue as I am making provisions for up to 3A at 5V and in testing the Raspberry Pi 3 did not exceed a current draw of 1A even at start up. According to research the maximum current
draw of a Raspberry Pi 4 in combination with a 7 inch touchscreen at 800*480 resolution will be 2.1A at 5.1V.

The touchscreen was chosen mainly due to price as well as the touchscreen functionality. I did consider building a controller consisting of about 5 buttons, but after careful consideration
I determined that it would be incredibly inconvenient potentially to the point that it would make the project unusable. The resolution was not really considered since quality is not
important for this project. 

The buck converter I will use for this project is an adjustable buck converter with a maximum current output of 3A.

I chose to use a 12V relay for this project because the standard voltage in a car is 12V. Other components like the BJT's and diodes were also chosen to be 12V tolarent

I will briefly discuss the sound problem. Any standard head unit in a car from this time as the audio amplifier already built in, in order to drive the speakers, but this project aims
to replace to standard head unit. Therefor in anticipation of this project I installed an amplifier and wired all my speakers to the amplifier. When the project is complete the 
Raspberry Pi will output via it's aux output into the RCA input of the amplifier allowing for sound to play through the speakers.

Interesting note:
It is worth noting that because the amplifier will draw power directly from the car and not through a fuse I installed an inline fuse on the 12V line running from the battery to the amplifier.
In this process I also learned that the alternator of a car, the part that keeps the battery charged and provides power to most electronics in the car when the car is running, can supply up 
to 200A while a car battery has two ratings, CCA and the constant current it can provide. CCA(Cold Cranking Amps) is the current a brand new battery can provide for 30 seconds at -18°C while
the constant current rating is the current a battery is rated to supply under normal driving conditions. Typical CCA rating is 400-600A while the constant current rating is about 30A.

Key Features

Feature A: A brief explanation of what it does.

Feature B: A brief explanation of what it does.

Feature C: A brief explanation of what it does.

Challenges & Learnings
This section is crucial for showing your ability to overcome obstacles. Talk about a specific problem you faced and how you solved it. End with a summary of what you learned.

Challenge:
"One of the biggest challenges was securely handling user authentication and authorization. I was initially using a simple token-based system, but I quickly realized it wasn't robust enough."

Solution:
"I decided to refactor the authentication process to use [JWTs with refresh tokens] and a secure [cookie-based storage system]. This ensured that user sessions were managed securely and provided a better user experience."

Learnings:
"This project taught me a great deal about API design, database optimization, and user experience (UX) principles. I also became much more proficient in [specific skill, e.g., asynchronous JavaScript] and learned the importance of writing thorough unit tests."

Installation & Setup
Provide clear, step-by-step instructions for getting the project up and running locally.

Clone the repository:
git clone [your-repo-url]

Navigate to the project directory:
cd [project-name]

Install dependencies:
npm install or pip install -r requirements.txt

Set up environment variables:
Explain what variables need to be set (e.g., API keys) and how.

Run the application:
npm start or python run.py

Usage
How does a user interact with the project? Provide a few examples or a simple walkthrough.

Future Enhancements
This shows you are forward-thinking. What would you do next if you had more time?

Add more unit and end-to-end tests.

Implement a feature for user personalization.

Optimize database queries for improved performance.

Acknowledgements
Thank any libraries, tutorials, or open-source projects that were particularly helpful.
