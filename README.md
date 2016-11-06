# Kenny Toastman and Andrew Crusty present: [LaserToasterino](http://www.naminum.com/append?q=laser%20toaster)
![This is toast.](https://raw.githubusercontent.com/ase1/421_521_final_project/master/resources/20161020_162631.jpg "This is toast.")

<a name="abstract">
### Abstract
Technological breakthroughs in the last decade have significantly altered the way we experience our everyday lives, from smartphones, smart TV's, and even IoT products like thermostats. One aspect of our lives, though, has not seen any improvements coming from technology for many decades-- toast. The goal of this project is to thrust the breakfast experience into the 21st century. We will create a device that allows you to wake up to a perfect piece of personalized toast. Laser etching will be used to burn images, a daily agenda, an inspirational quote, or the day’s headlines right onto a piece of bread. The device can be used immediately on command, or can be scheduled to have your perfect toast ready for you, right when you wake up. The image to be printed could be a selfie (or other inferior photo) that you upload or content from the Internet, allowing for an entirely customizeable breakfast.

The device will be comprised of a laser, an enclosure with controls, and a Raspberry Pi retrofitted onto an old 3D printer. Stepper motors will control the position of the laser along the toast, and the power of the laser will be modulated at each point to create different toasting patterns. Software will be developed to combine photos, Web-scraped text, and more into a grayscale image to be burned on the toast, and it will then generate G-code for printing. This project will aim to recreate the toaster experience using an Arduino to control the knobs, dings, and doors that we’ve all grown to love.

### Table of Contents
1. [Use Flowchart] (#flowchart)
2. [Software Approach] (#software)
3. [Hardware Approach] (#hardware)
4. [Brainstorming] (#brainstorming)
5. [Safety] (#safety)

<a name="flowchart">
### Use Flowchart
This flowchart shows the processes and decisions that are made to output the admittedly scrumptious final product. 
![Flowchart](https://raw.githubusercontent.com/ase1/421_521_final_project/master/resources/flowchart.png "Flowchart showing use cases.")

<a name="software">
### Software Approach
We'll be using three boards for this project: a Raspberry Pi, a RAMBo motherboard, and an Arduino Uno. The three main facets of the software are controlling the motors/laser, generating and processing images for toasting into G-code, and displaying a graphical user interface to allow the user to select what they want on their toast. 

<a name="hardware">
### Hardware Approach
We have an old 3D printer, inherited from legendary Rice alum Ravi Sheth. We're using this as the base of our project since it already has the dimensional movement that our plotter will require. We want to take apart the printer, remove unnecessary components, and reassemble it inside of an enclosure. We need to install a couple of Arduino-controllable actuators to put some polish on the experience. For EHS reasons, we aren't allowed to use a laser powerful enough to cause blindness, so as a proof of concept, we'll mount a 5mW laser on the machine and test using photographic paper. 

The modified 3D printer hardware was modeled in SolidWorks, and the enclosure was created around it. The enclosure is made of birch plywood, which is fine because the laser isn't powerful enough to burn through it. For the interface with the user, we're using a Raspberry Pi touchscreen display and a couple buttons and knobs for tactile control. A sliding door will shield the user from the laser during operation. 


<a name="brainstorming">
### Brainstorming
We spent the weekend coming up with ideas, and the crowd favorite is a toast printer. You've seen Jesus toast, and we want to take that one step further. Imagine waking up, checking your calendar, reading the newspaper, and ravenously scrounging for something to eat in the morning. Our idea proposes to combine early morning activities using a toaster with a controllable toast pattern. We're considering creating an appliance that internally works like a laser etcher, with the functions of a toaster. We have a non-working 3D printer that we're willing to scavenge for parts. We plan to design the hardware and software experience. Software for generating G-code for laser etching already exists, so we'd probably implement that and focus our efforts on image processing, content production, and hardware control. 

 - Sensors: 
   - Check if bread is on the plate
   - Check door status (open/closed)
   - Check power level dial
   - Button for start
   - Laser temperature

 - Actuators: 
   - Emergency stop button
   - Eject button (might be fun to have this under a plastic shield)
   - Must include spring actuation and self-deployed toast parachute
   - Move platform
   - Open/close door
   - Ring bell when complete
   - Laser ventilation
   - Alarm clock function that wakes you up to fresh toast

 - If we have time (we won’t have time):
   - Toast flipper
   - Camera on toast (timelapse?) (Twitter?)
   - Butter melter and liquid butter spreader
   - Photo booth


##### Discrete subprojects: 
 - Create lasercutter functionality - hardware
   - Disassemble printer
   - Buy parts
   - Figure out power requirements
   - Safety measures
   - Control 
 - Data grabbing from the internet
   - Date
   - Inspirational quotes
   - News
   - Notifications
 - Compile into an image for image processing
   - Image processing (see this: http://nebarnix.com/img2gco/)
   - Take existing image and convert to grayscale
   - Create an array of laser voltages per pixel
     - We can just always go line-by-line if that’s easier
   - Send to laser cutter
   - Arduino stuff


<a name="safety">
### Safety (for a device with a full-powered laser)
We can break safety concerns down to three categories: health, fire, and electrical. 

__Health__. The most threatening safety concern is health - pointing a laser at a person for too long could cause blindness or burns. The easiest countermeasure is to buy the lowest-powered laser that will still accomplish our goal. We're ready to do some testing on Thursday using the OEDK laser cutter to see what powers we realistically need for etching the toast, but online research has shown that we won't need more than 1-2 W. For testing, we'll want to modulate that power down to the mW range (typical laser pointers are 5-10 mW) so we can see what we're doing but aren't creating any threat. The final device will have a door that seals the inside off from the outside, so there can be no leakage of light. We can make this door into a physical switch, so the laser can't receive power unless this door is closed. For testing, we'll also have to get some laser safety glasses, which depend on the wavelength of light produced by the laser. 

__Fire__. Another big one, also mostly solved by choosing the right laser. We want to do some testing on the laser that we eventually choose, but if need be, we can solder on a heatsink and provide forced convection with a fan. I don't expect there to be too much smoke produced, since normal toasters don't produce an unreasonable amount of smoke and we plan to only etch the surface of the toast. We want to make the enclosure out of think aluminum or 1/4" wood - the laser shouldn't be high-powered enough to penetrate or ignite either of these. 

__Electrical__. Good insulation practices should resolve any concerns. 
