# Tutorial 1: Getting Started
## Important
**This tutorial assumes that you are using `v0.1.12a` or higher.**

## Step 1 - Download and Install Engine Simulator
Follow the instructions for downloading/installing *Engine Simulator* on the [main page](../../README.md).

## Step 2 - Start Engine Simulator
Navigate to `bin/` and run `engine-sim-app.exe`

![Alt text](assets/screenshot_01.PNG?raw=true)

After double clicking the `.exe` *Engine Simulator* should start and open with a default engine.

![Alt text](assets/screenshot_02.PNG?raw=true)

**If an error pops up saying that you're missing a DLL, then run the `.exe` files in the `installation/` folder**

## Step 3 - Adjust the Simulation Performance
*Engine Simulator* requires a fairly powerful CPU to run well. However, you can still adjust the performance to work with slower CPUs.

To do this, we first check the RT/DT gauge.

![Alt text](assets/screenshot_03.PNG?raw=true)

A value around 70 is ideal. Above 80 and you will notice audio distortions or a drop in framerate. If your gauge looks like this, you need to adjust the simulation frequency:

![Alt text](assets/screenshot_04.PNG?raw=true)

The **simulation frequency** is the internal simulation "framerate" or tickrate. It is displayed in the *Frequency* gauge:

![Alt text](assets/screenshot_05.PNG?raw=true)

To adjust the tickrate, hold the `n` key and scroll down with your mouse. Once the RT/DT gauge stabilizes at around 70, you've found a good simulation frequency for your PC.

**IMPORTANT:** different engines have different performance requirements so you may have to adjust this differently for different engines

**If you still experience audio distortions even after following the above procedure**, check the `IN. BUFFER` gauge. If the gauge is erratic or moves very far to the right or left, your CPU is struggling to keep up with the real-time audio processing. There is no solution to this right now but a fix is planned for future versions. Different engines have different audio processing requirements and so they may work on your PC. Typically engines with 2 or more exhaust systems tend to be the most expensive.

## Step 3 - Start the Engine
The system status lights in the bottom left corner show the states of the ignition, starter, dynamometer and dynomometer hold functions. For now, we're only concerned with the ignition and starter lights.

![Alt text](assets/screenshot_06.PNG?raw=true)

### 1. Turn the ignition on with the `a` key
To turn the ignition on and off, press the `a` key. You should see the ignition indicator light turn on. In a real spark ignition engine, "ignition" indicates that the ignition module is active and the spark plugs will fire. It has the same meaning in *Engine Simulator*.

### 2. Enable the starter with the `s` key
The starter is a small electric motor that is fitted to most internal combustion engines. It spins the motor initially so that it can start and then run on its own power. Pressing the `s` key will engage the starter. Once the engine is running under its own power, you can let go of the `s` key.

### My audio sounds messed up. What do I do?
If you still have strange audio artifacts like skipping or looping even after adjusting the simulation frequency, the bottleneck may instead be on the audio side of things. There are no adjustments in *Engine Simulator* to solve this right now but it's an area we're actively researching. You may have better luck with a different engine but it's likely that your CPU will struggle regardless of which engine you select. Sorry about that! Look out for future updates which will make the audio processing faster and easier to run on slower CPUs.

## Step 4 - Revving the Engine
To rev your engine like a maniac, you can use the following buttons:

1. `q` - Light throttle
2. `w` - Light/part throttle
3. `e` - Part throttle
4. `r` - Full throttle

To finely adjust the throttle, press the `space` key and scroll up and down with mouse. You can see the exact throttle amount in the "Throttle" instrument on the right.

![Alt text](assets/screenshot_07.PNG?raw=true)

## Step 5 - Performing a Dyno Test
A dynamometer (dyno) is a device which measures the output torque of an engine and converts that to a power output. By default, torque is measured in lb-ft and power is measured in horsepower.

The dyno in *Engine Simulator* has more features than a real-life dyno. Since it is a theoretical dynamometer, it can both act as an engine brake and it can also *motor* the engine. Motoring an engine means to spin it using an external motor.

### 1. Enable the dynamometer with the `d` key
If this stalls your engine, it's probably because the engine idles higher than the minimum speed supported by the dyno (by default it is 1000 rpm). In this case, simply apply part throttle to keep the engine from stalling.

### 2. Give the engine full-throttle by pressing the `r` key
Dyno tests in real-life are usually conducted at full-throttle. You could nonetheless do a part-throttle dyno test if you really want to.

### 3. Wait for the dyno to reach the engine's redline
The dynometer will continue increasing its speed until either it reaches the engine's redline or it senses that the engine can no longer apply a positive torque to the dynamometer (ie. the engine requries external help to maintain engine speed).

When the dyno can no longer increase its speed, it is automatically disabled and the maximum torque and power are displayed on the "Torque" and "Power" gauges.

![Alt text](assets/screenshot_08.PNG?raw=true)

To get a read-out of the peak torque and power, press the `i` key. The read-out will be displayed in the status text in the top left corner.

![Alt text](assets/screenshot_09.PNG?raw=true)

## Step 6 - Visually Inspecting the Engine

*Engine Simulator* offers a variety of ways to look around and inspect your engine. The **Engine Visualization** display in the center of the screen is a 2D visual representation of the engine you are testing.

### Panning and zooming
1. Pan the display by clicking on the Engine Visualization and dragging with the mouse
2. Zoom in and out by placing the cursor within the Engine Visualization window and scrolling with the mouse wheel

### Warping time
The engine might be a little hard to see while it's running. To slow down time, use the following keys:
1. `1` key - 1/10 speed
2. `2` key - 1/100 speed
3. `3` key - 1/200 speed
4. `4` key - 1/500 speed
5. `5` key - 1/1000 speed

The current simulation speed can be seen in the **1 / Speed** gauge.

![Alt text](assets/screenshot_10.PNG?raw=true)

### Change Display Layout
Pressing the `tab` key will change between display layouts.

#### Layout 1 (default)
![Alt text](assets/screenshot_11.PNG?raw=true)

#### Layout 2
![Alt text](assets/screenshot_12.PNG?raw=true)

#### Layout 3
![Alt text](assets/screenshot_13.PNG?raw=true)

## Step 7 - Drive a Vehicle
*Engine Simulator* comes with a simple vehicle simulation with a manual transmission. Launching is the same as launching a vehicle in real-life but is somewhat complicated by the lack of smooth pedal inputs. Nontheless, it can be done (though controller/steering wheel support is planned).

### 1 - Press the clutch pedal with the `shift` key
The `shift` key presses the clutch in (ie disconnects the transmission from the engine). The pressure applied by the clutch disk on the flywheel is shown in the **Clutch** gauge. 0 is equivalent to the clutch pedal being completely pressed.

![Alt text](assets/screenshot_14.PNG?raw=true)

### 2 - Give the engine part throttle with `w` or `e`
This will depend on the engine. If you want to smoke your clutch completely, you can bounce off the rev-limiter instead of holding part-throttle. For some engines, it might be too difficult to launch without the fine control of a clutch pedal. In that case, simply holding the engine at full throttle will suffice.

### 3 - Shift into first gear by pressing the `up` key
Gears are changed using the `up` and `down` arrow keys. The current gear is displayed in the **Gear** display.

![Alt text](assets/screenshot_15.PNG?raw=true)

Release the clutch pedal by releasing the `shift` key. To smoothly release the clutch, hold the `space` key simultaneously.

### 4 - Adjust the throttle using `q/w/e/r` until your desired rate of acceleration is achieved

### 5 - Shift gear
To change to a higher gear, the same procedure as a real car is followed. Press the clutch with `shift` then the `up` or `down` arrow to change gear. Once you've selected your intended gear, release the clutch by releasing `shift`. The engine's current RPM and the vehicle's current speed are shown prominently in the **Engine Speed** and **Vehicle Speed** gauges.

![Alt text](assets/screenshot_16.PNG?raw=true)

## Step 8 - Measuring Engine Braking
An engine's braking capabilities can be measured using the dynamometer as well using the hold feature. The dyno hold will *motor* the engine at a rate of your choosing.

### 1 - Enable the hold feature by pressing the `h` key
Nothing will happen immediately upon enabling the hold feature because it also requires the dynamometer to be active.

### 2 - Enable the dynamometer by pressing the `d` key
The dynamometer will now spin the engine at the speed shown in the "Dyno. Speed" gauge.

### 3 - Change the dyno speed by holding `g` and scrolling up/down with the mouse wheel
After adjusting the speed, you can read the measured torque and power of the engine which will usually be negative if the throttle is closed.

![Alt text](assets/screenshot_17.PNG?raw=true)

## Step 9 - Changing Engines
To change the engine being simulated, press on the "Load Script" button in the upper left corner.

![Alt text](assets/screenshot_18.PNG?raw=true)

Then, navigate to the location that you unzipped *Engine Simulator* to. To load one of the engines that appeared in AngeTheGreat's video series, open an engine in `assets/engines/atg-video-1/` or `assets/engines/atg-video-2/`.

Allow a little time for the script to load and for the simulation to stabilize.

![Alt text](assets/screenshot_19.PNG?raw=true)

Once the script is loaded, you can interact with the engine in the same way as described in the previous steps.

## Step 10 - Changing to Metric Units (optional)
If you'd like to change to metric units, click on the "Load Theme" button in the upper left of the window.

![Alt text](assets/screenshot_20.PNG?raw=true)

Navigate to the location where you unzipped *Engine Simulator* then go to `assets/themes` and choose `default_metric.mr`. You only need to set this once and *Engine Simulator* will remember your theme next time you open the application.

![Alt text](assets/screenshot_21.PNG?raw=true)

## "Blown" Engines
It can sometimes happen that an engine "explodes" or disappears off the screen. This means that the simulator has reached an unsolvable state from which it cannot recover. This *shouldn't* happen under normal conditions but can happen if you lower the simulation frequency too much or try to run a physically impossible engine.

There is no way to bring the engine back after it "explodes" in this way. The best option is to press the "Reload" button in top left corner or pressing the `enter` key which will reset the engine and the simulation.

![Alt text](assets/screenshot_22.PNG?raw=true)

## Conclusion
This tutorial covered all the basics of operting *Engine Simulator*. The next tutorial will teach you how to download engines from the community portal and run them in *Engine Simulator*.

- [Tutorial 2: Running Community Engines](../02_using_community_engines/02_using_community_engines.md)
- [Back to main page](../../README.md)
