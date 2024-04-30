[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/2TmiRqwI)
# final-project-skeleton

    * Team Name: UPenn Fire Department
    * Team Members: Isaac Gray, Oliver Hendrych
    * Github Repository URL: https://github.com/ese3500/final-project-upenn-fire-department
    * Github Pages Website URL: https://ese3500.github.io/final-project-upenn-fire-department/
    * Description of hardware: See '9. Components' below 

## Final Project Proposal

### 1. Abstract

In a few sentences, describe your final project. This abstract will be used as the description in the evaluation survey forms.

The UPenn Fire Department Team is building a semi-autonomous remote controlled firetruck. Using wireless communication to control the truck itself and thermal imaging to control the water gun, the truck will be able to go into areas not normally accessible by humans to put out fires. The thermal imagining will allow the truck to detect the direction and location of the fire, removing the need for direct human oversight of the relative positions of the fire truck and the fire.

### 2. Motivation

What is the problem that you are trying to solve? Why is this project interesting? What is the intended purpose?

The UPenn Firetruck will put an end to fires that are normally inaccessible to humans, and/or supervise over areas to detect fires. This project incorporates multiple different sensors and actuators, including sensors for heat and distance, as well as actuators for drive, steering, aiming, and blasting water, meaning that it is a culmination of many of the different, interesting means of control we have learnt through the semester, along with some more. Its intended purpose is to find heat sources (fires) and cool them down (with water).

### 3. Goals

These are to help guide and direct your progress.

The UPenn Firetruck will be constructed such that it can act in two modes: Manual and Overwatch. Manual will involve a user directly controlling the truck movement and possible the water gun, and will allow human operators to put out fires from a distance, and in places usually unaccessible to human firefights. Overwatch will be an always-on mode that uses the thermal imaging to scan for fires or other high-heat sources.

### 4. Software Requirements Specification (SRS)

Formulate key software requirements here.

#### Overview

The project will mainly revolve around taking in sensor input to determine motor controlled output, and using that feedback loop to operate. Wireless communication, the ultrasonic sensor, and the thermal camera will inform movement, which will cause the readings from the ultrasonic sensor and thermal camera to change. The thermal imaging will inform the water turret aiming and firing, which will in turn change the thermals seen by the camera.

#### Users

The users are anybody who needs to be able to put out fires in cramped spaces and/or autonomously. This could be people with complex cooling/heating systems, with cramped access ducts. Or even farmers overseeing grain stockpiles in hot, dry summers, who want to be able to put out fires without flooding their whole crop with water and causing it all to mold. And of course, the UPenn Firetruck is another tool for regular firefighters to add to their arsenal that can be applied in a situation where debris has caused areas to become inaccessible to humans.

#### Definitions, Abbreviations

* MT = Motors used to drive
* MC = Microcontroller
* RC = Remote Communication
* TI = Thermal Imaging
* US = Ultrasonic sensor
* WT = Water turret (and the motors used to drive it)
* WG = Water gun (and the motor used to fire it)
* WP = Waterproofing (shell for other means)

#### Functionaility

SRS 01 - 'The US shall be sampled as often as possible, and results smoothed/averaged to reduce the effect of noise'

SRS 02 - 'MT shall be controlled using PWM outputs from MC to determine speed'

SRS 03 - 'The hottest heat source in the TI shall be indentified and targeted by WT'

SRS 04 - 'If a sufficiently hot heat source is identifed by `SRS 03`, WG shall be fired'

SRS 05 - 'Output from US as specified in `SRS 01` shall prevent MT from driving device into the wall'

SRS 06 - 'Along with US input from `SRS 05` and `SRS 01`, RC shall inform output to MT using tank controls'

SRS 07 - 'Manual control of WT and WG should be possible through use of RC'

### 5. Hardware Requirements Specification (HRS)

Formulate key hardware requirements here.

#### Overview

The hardware shall be broken down into two parts: mechanical and electrical. The main goal of the mechanical section is to provide avenues to sense and control using the electrical. This includes mounting of MT, US and TI, as well as a mechanism to control WT and WG. Finally, the mechnical section should provide at least some level of WP. The electrical section will define the elements used to control each of these actuators, and the sensors that inform the MC.

#### Definitions, Abbreviations

* MT = Motors used to drive
* MC = Microcontroller
* RC = Remote Communication
* TI = Thermal Imaging
* US = Ultrasonic sensor
* WT = Water turret (and the motors used to drive it)
* WG = Water gun (and the motor used to fire it)
* WP = Waterproofing (shell for other means)

#### Functionaility

HRS 01 - 'MT shall be controlled through driving circuit, which is in turn shall be driven by MC'

HRS 02 - 'RC shall be provided by Feather ESP32 or other means, connected to MC'

HRS 03 - 'TI shall be provided by camera, which should be cheap and low resolution'

HRS 04 - 'TI shall be connected to MC, and communicate through SPI'

HRS 05 - 'TI shall be mounted to front of device, or should be mounted to WT'

HRS 06 - 'US shall be mounted to front of device, or optionally to mounted to WT'

HRS 07 - 'WT shall provide method of yaw rotation of WG'

HRS 08 - 'WT should provide method of pitch rotation of WG, or WG should be controllable in distace'

HRS 09 - 'WP shall provide protection of MT, MC, RC, TI, and US from liquids shot by WG'

### 6. MVP Demo

What do you expect to accomplish by the first milestone?

By the first milestone, we plan to have a working car that is simply able to drive around. Separately, we plan to have a working water turret or at least a mechanical mock-up of the water gun and a method to aim and actuate it, as well as a means of communicating between the thermal imaging and the microcontroller. Finally, we will have decided on and devised a method for wireless communication with the firetruck, whether that be using Blynk and the Feather ESP32, radio waves, or other means.

### 7. Final Demo

What do you expect to achieve by the final demonstration or after milestone 1?

By the final demonstration, we will have combined all the separate elements that we prepared in milestone one. This includes attaching the water gun to the firetruck and controlling it with the microcontroller (and thermal imaging), and linking the wireless communication to the microcontroller. Additionally, to protect the sensitive electronics on the firetruck, we will have some shell / outer design for the firetruck or other waterproofing.

### 8. Methodology

What is your approach to the problem?

Our approach will be at first split across the different aspects of our project. That is, the microcontroller, the thermal imaging, the water gun, the car control, power management, and the wireless controller. This will allow us to work on different parts in parallel in order to increase efficiency. Importantly, as we begin designing these separate processes, we will defines the interface by which each one interacts with the others. This is to make the next step, integration, much easier and faster. We will combine all the different aspects of the project and use the microcontroller to bring them all together.

Putting out fires that one cannot see directly is a difficult task. Evidently, some other device able to be dispatched to put our these fires is needed (i.e. the UPenn Firetruck). However, this does not solve the problem of the lack of direct visual confirmation. Video streaming is costly and complex. The more that can be done on the firetruck, the better. As such, thermal imaging is necessary to determine the source of the fire and put it out. Extra care and sensors are needed to make sure the firetruck does not get stuck or break itself by ramming into a wall.

### 9. Components

What major components do you need and why?

The major components we will need are:

* The microcontroller: to bring all the aspects of the project together give a platform for computation on the firetruck
* A thermal camera: can be cheap and low resolution, but necessary so that the firetruck can determine where the fire is to aim the water gun
* Motors and servos: To be able to drive the car, actuate the water turret, and fire the water gun
* Ultrasonic sensor: To prevent the car from breaking itself by ramming into a wall when the user cannot see it
* Wireless communication module: To allow remote control of the firetruck
* Shell or other waterproofing: Both for visual effect and to protect the sensitive electronics on the firetruck

### 10. Evaluation

What is your metric for evaluating how well your product/solution solves the problem? Think critically on this section. Having a boolean metric such as “it works” is not very useful. This is akin to making a speaker and if it emits sound, albeit however terrible and ear wrenching, declare this a success.
It is recommended that your project be something that you can take pride in. Oftentimes in interviews, you will be asked to talk about projects you have worked on.

The measures of success we will have for this problem are twofold: movement and sensing. The wireless communication and actuators on the car will work towards the movement: being able to control the car remotely is critical to overall performance, as is it being able to drive. Aiming the water turret is critical as well, but could possibly be sidestepped with driving to aim. The thermal imaging and ultrasonic sensor will help with sensing: being able to determine where the fire is with relative accuracy, and preventing the firetruck from ramming itself into a wall would be nice as well, but can also be sidestepped with rugged design. Waterproofing is an auxiliary goal, but would be nice to prevent single-use electronics.

### 11. Timeline

This section is to help guide your progress over the next few weeks. Feel free to adjust and edit the table below to something that would be useful to you. Really think about what you want to accomplish by the first milestone.

| **Week**            | **Task** | **Assigned To**    |
|----------           |--------- |------------------- |
| Week 1: 3/24 - 3/31 |  Mechanical Designs and hardware/software layout  |   Isaac and Oliver, respectively   |
| Week 2: 4/1 - 4/7   |  Fabrication and Motor control started; sensor and wireless communication basics  |     Isaac and Oliver, respectively           |
| Week 3: 4/8 - 4/14  |  Fabrication finished and motor control finalized; overarching control (sensing and actuating) logic finished    |    Isaac and Oliver, respectively      |
| Week 4: 4/15 - 4/21 |   First milestone goals (see above)   |     Team effort     |
| Week 5: 4/22 - 4/26 |   Final goals (see above)   |        Team effort   |

### 12. Proposal Presentation

Add your slides to the Final Project Proposal slide deck in the Google Drive.

## Final Project Report

Don't forget to make the GitHub pages public website!
If you’ve never made a Github pages website before, you can follow this webpage (though, substitute your final project repository for the Github username one in the quickstart guide):  <https://docs.github.com/en/pages/quickstart>

### 1. Video

[Insert final project video here]

### 2. Images

[Insert final project images here]

### 3. Results

What were your results? Namely, what was the final solution/design to your problem?

#### 3.1 Software Requirements Specification (SRS) Results

Based on your quantified system performance, comment on how you achieved or fell short of your expected software requirements. You should be quantifying this, using measurement tools to collect data.

These are our software requirements that we created when starting our project. We will go through each one and evaluate how well, if at all, the requirement was achieved. 

**Definitions for reference** 
* MT = Motors used to drive
* MC = Microcontroller
* RC = Remote Communication
* TI = Thermal Imaging
* US = Ultrasonic sensor
* WT = Water turret (and the motors used to drive it)
* WG = Water gun (and the motor used to fire it)
* WP = Waterproofing (shell for other means)

SRS 01 - 'The US shall be sampled as often as possible, and results smoothed/averaged to reduce the effect of noise'

This SRS was met in full. By using timers for the trigger and echo, we were sending out triggers soon after echos were received, and also sent them after a timeout (if no echo was received). These results were smoothed with a configurable number of values to include in the average, for which we went with 4 in the final design for a mix of accuracy and quick response time.

SRS 02 - 'MT shall be controlled using PWM outputs from MC to determine speed'

We found that it was not necessary to use the PWM outputs from the MC in order to control the MT because the motors acted at a fine speed to begin with. Also, the ATMega would not have had enough timers to control all 4 of the MT outputs individually, in conjuction with our other features. A simple but sufficient system to control the front/back left/right motors with just the pin outputs was used.

SRS 03 - 'The hottest heat source in the TI shall be indentified and targeted by WT'

This SRS was met in full. By querying the entire output of the TI over I2C, we were able to get all the values within the 8x8 frame that the TI sensed. An I2C watchdog was implemented so that if no response was detected from the TI, the MC would restart communication, as it is likely message(s) were lost. Additionally, the TI only operated at 10Hz (max), and we were able to sense all values within that time, so no data was lost. The hottest heat source was identified with a simple maximum. However, we ran into some issues as some sensors within the 8x8 array were biased to detect a higher temperature than others. As such, we chose to neglect those values when finding which pixel was hottest. The heat source was target by WT, as we would turn the katzbot if the heat source was determined to be on the corresponding edge of the TI readings. It would therefore center on the target and prepare to fire.

SRS 04 - 'If a sufficiently hot heat source is identifed by `SRS 03`, WG shall be fired'

This SRS was met in full. A configurable threshold was used to determine when the WG was fired. If the hottest pixel as identified in `SRS 03` was above this threshold, WG would fire. In addition, in order to prevent the water from splashing back, the US output from `SRS 01` would be used to determine if we were too close to the target (as according to another configurable limit). If so, then WG would not fire.

SRS 05 - 'Output from US as specified in `SRS 01` shall prevent MT from driving device into the wall'

This SRS was met in full. A configurable limit for how close the katzbot would get to the wall while still moving forward was set. In autonomous mode, the MT would be set to turn right (in place) instead whenever the US measured too small of a distance. In manual mode, the forward motors would not be enabled if a all was detected.

SRS 06 - 'Along with US input from `SRS 05` and `SRS 01`, RC shall inform output to MT using tank controls'

This SRS was met in full. By using inputs from the ESP32 Feather in combination with Blynk.io, we were able to remotely control the katzbot using our laptops or phones. It was with tank controls that one can move the robot, with individual buttons for controlling the front/back left/right motors. Additional software checks were added to prevent the user from trying to move both forward and back on the same side (left/right).

SRS 07 - 'Manual control of WT and WG should be possible through use of RC'

While the WT (katzbot itself) could be controlled using RC, the recommendation of also controlling the WG was not met due to the limitations of a free Blynk.io account. With only 5 inputs available, 4 were used for movement controls and 1 was used to determine which mode (autonomous or manual) the MC would operate in. However, given the amount of configurability in the WG behavior and with the use case commonly being in areas not directly visible by the user, we determined this semi-autonomous mode of controlling the WG was acceptable.

#### 3.2 Hardware Requirements Specification (HRS) Results

Based on your quantified system performance, comment on how you achieved or fell short of your expected hardware requirements. You should be quantifying this, using measurement tools to collect data.

These are our hardware requirements that we created when starting our project. We will go through each one and evaluate how well, if at all, the requirement was achieved. 

**Definitions for reference** 
* MT = Motors used to drive
* MC = Microcontroller
* RC = Remote Communication
* TI = Thermal Imaging
* US = Ultrasonic sensor
* WT = Water turret (and the motors used to drive it)
* WG = Water gun (and the motor used to fire it)
* WP = Waterproofing (shell for other means)

HRS 01 - 'MT shall be controlled through driving circuit, which is in turn shall be driven by MC'

This was achieved by using a prebuilt motor driver, the katzbot. This allowed us to only need to control the motor signal with out ATMega. This allowed us to not have to worry about the actual motor drive which would have been much more difficult and outside the scope of the class. Additionally, the load on the MC pins itself was much reduced.

HRS 02 - 'RC shall be provided by Feather ESP32 or other means, connected to MC'

This HRS was also acheived. We used the Blynk.io dashboard along with an ESP32 feather to wirelessly communicate between a "home base" (a laptop or phone) and the bot. From there we connected the ESP32 to a level shifter which then went to the the ATEMEGA and we drove the motor using pin change interrupts from those inputs.

HRS 03 - 'TI shall be provided by camera, which should be cheap and low resolution'

This we also acheived using a AMG8833 infared camera which was not super cheap but it was within budget at ~45 dollars, and was the cheapest, easy to use option found. It was realtively low resolution but worked perfectly for our purposes. It has 64 pixels but a relatively narrow field of view, so for what it could see it was detailed enough to sense large areas of heat which is what we were scanning for. 

HRS 04 - 'TI shall be connected to MC, and communicate through SPI'

Here our final project slightly differed from the hardware specifications. We ended up selecting a TI that communicated with I2C rather than SPI. This made hardware even easier only needing to route two wires especially with how many wires we had to use. However it did lead to some software issues that we discussed in the software specifications section. The relatively smaller bandwidth of I2C was not an issue as the TI only sampled at 10Hz, meaning we were able to read everything necessary within a frame of the TI.

HRS 05 - 'TI shall be mounted to front of device, or should be mounted to WT'

The TI ended up being mounted right in the center and front of the bot. However we changed the mechanical design of our project to remove the WT and instead used the katzbot to hold everything. This meant that the TI wasn't connected to the WT but it was connected to the front of the device. 

HRS 06 - 'US shall be mounted to front of device, or optionally to mounted to WT'

As described above, we did not use a turret to hold our sensors and instead attached both the US and TI to the front of our katzbot. The US was slightly off center to accomadate the TI which we wanted to be centered with the WG in the middle. We thought this was the best option because we assumed that due to the small size of the bot and the small offset the US had there wouldn't be any obstacles too narrow that the US would miss them and the bot would crash. This assumption turned out to be true and even with the chairs and peoples legs in Detkin we did not have any issues with crashing the bot. 

HRS 07 - 'WT shall provide method of yaw rotation of WG'

As discussed previously, since we did not have a WT this hardware specification was not possible to implement. Instead of providing yaw through a rotatable WT, the algorithim that we wrote to move the bot and shoot would rotate the bot to center on a fire and then the WG would only have to shoot straight. This allowed us to simplify our design while still maintaining functionality. 

HRS 08 - 'WT should provide method of pitch rotation of WG, or WG should be controllable in distace'

We also removed the need for pitch rotation by angling our acryllic so that our WG was pointed parallel to the ground. This combined with a known force and change in angle of the servo allowed us to fix the distance that the WG was able to shoot. Using these we included in the algorithm that as long as the hot object was between the minimum and maximum distances reached by our horizontal WG (~10cm to 100cm) it would shoot and if it were outside this range it would move to be in that range before firing the WG. 

HRS 09 - 'WP shall provide protection of MT, MC, RC, TI, and US from liquids shot by WG'

We achieved this HRS by using clear laser cut acryllic glue to the sides and with a plate glued across the top as well. We glued the acryllic at a downward sloping angle and with a cantileverd front (which can be seen in the images of our bot). This allowed any water that did end up dripping to be forced down in front and ahead of the bot so none would get on the bot. In testing even when pouring water onto the acryllic plate -- which is much more water than we would ever expect from a leaking WG -- the bot was kept completely dry.

### 4. Conclusion

Reflect on your project. Some questions to consider: What did you learn from it? What went well? What accomplishments are you proud of? What did you learn/gain from this experience? Did you have to change your approach? What could have been done differently? Did you encounter obstacles that you didn’t anticipate? What could be a next step for this project?

Isaac:
This project was very enjoyable and rewarding overall however there were a couple of issues and difficulties that if we were to do it again I would make sure to avoid or fix. I think the main one was we definitley started a bit late. The main issue with this is that we didn't have enough time to order some of the parts we would have liked including more water guns to attach to our bot as well as Blynk premium which we only realized we needed the day before demo day. Another issue that arose from lack from planning was we didn't have as much time as we would have liked to test our bot before demo day. This wasn't as bad as an issue for us specifically because we got a bit lucky and our project worked very well with minimal testing, but it just as easily could have had a bunch of small bugs that we wouldn't have been able to fix due to lack of time. Overall other than this small issue I think this project went extremly well with minimal large issues that had us stuck for long periods of time. Instead we were really able to focus on creating and innovating on our product instead of just thinking about what is causing bugs. This allowed us to have a lot of fun adding things like sirens and LEDs clear laser cut acryllic for waterproofing. One of the obstacles we encountered was powering the bot. We had a bunch of features and that added up to the point to where the katzbot couldn't provide enough power when it was turning quickly (we think this is due to the inductive spikes in the motors) this led to the ATMega latching sometimes and we couldn't figure it out for a while until we powered it seperatley from the rest of the board and there was no latching issue. This issue brought in concepts from previous classes which was fun that we used them to solve this strange bug, and once we found it it was a realitvely easy fix. One small thing on the car that I am very proud of is that all the blinking LEDs are powered off of one GPIO pin. We were running out of pin space, so we had to get creative and so I had the GPIO pin driving both a pmos and an nmos to get complementary switching while saving pin space. Overall I had a lot of fun with this project and I am happy we were able to make something consistent with a very cool application that could maybe one day help the world. One interesting thing that I would love to do next is add more infared sensors, more water guns, and then improve the autonomous algorithm to the point where it can seek out fires and put them out with more water power than just one small squirt gun which was a proof of concept more than anything. An actual water pump to deliver non-trivial amounts of water would be ideal. 

Oliver:
Overall, this project went well and I am very satified with our final result. I learned quite a bit, especially about I2C -- both about how the protocol works in full in practice, and how the ATMega works with it. There were certainly some issues that could have caused a lot of headache, but prior experience from this class and the ATMega combined with experience from other classes and extracirricular activites prepared us and we were able to solve them quickly. I do agree that we started late, and we are a little lucky that we were able to accomplish everything we wanted in time. I am also proud, however, of our ability to diagnose and fix the issues we did encounter. When the ATMega would randomly latch, we were able to diagnose that it was due to a power issue, and moved the ATMega to a different power supply. This caused its own separate issue of alignment with the I2C thermal camera, as one starting before the other could (and did) cause messages to be lost. We were able to diagnose this and then implement a watchdog relatively quickly to fix it. I am also relatively proud of our code structure. We use a multitude of different timers and interrupts for everything, including the ultrasonic sensor, LEDs, siren, servo, and thermal camera, and had to maintain a clean codebase in order to avoid issues. We were able to accomplish all of this on the ATMega, with lots of configuration options. I very much enjoyed our very mean-looking watergun-servo combo, and it was cool that it was able to shoot a fair distance. We had to change our approach in some respects, mostly to simplify the process in order to actually meet our required deadline and accomplish what was important and relevant to the class. For example, we did not have a separate water turret, we just attached the watergun to the katzbot and turned that instead. However, this did not impact functionality greatly but simplified the work we had to do considerably. In terms of what could have been done differently, we definitely could have started integration a little earlier. We had the ultrasonic sensor, thermal camera, servo, wireless, and katzbot working seperately for a while, but putting them together was more effort than expected. An unanticipated obstacle was the Blynk.io limit of 5 buttons to control the virtual pins. This mean that we weren't able to shoot the watergun manually because all inputs were full determining driving and mode. Overall, the project was very fun and I am very happy with how it turned out. A next step would be to add more firepower, and to have even better autonomous code.

## References

Fill in your references here as you work on your proposal and final submission. Describe any libraries used here.

No libraries were used aside from the ATMega interface provided by AVR and microchip studio. The references used were soley the datasheets for the ATMega, thermal camera, ultrasonic sensor, ESP32 Feather, and other components.

## Github Repo Submission Resources

You can remove this section if you don't need these references.

* [ESE5160 Example Repo Submission](https://github.com/ese5160/example-repository-submission)
* [Markdown Guide: Basic Syntax](https://www.markdownguide.org/basic-syntax/)
* [Adobe free video to gif converter](https://www.adobe.com/express/feature/video/convert/video-to-gif)
* [Curated list of example READMEs](https://github.com/matiassingers/awesome-readme)
* [VS Code](https://code.visualstudio.com/) is heavily recommended to develop code and handle Git commits
  * Code formatting and extension recommendation files come with this repository.
  * Ctrl+Shift+V will render the README.md (maybe not the images though)
