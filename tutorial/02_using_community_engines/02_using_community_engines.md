# Tutorial 2: Using Community-made Engines
## Important
**This tutorial assumes that you are using `v0.1.12a` or higher.**

## Introduction
Changing engines has historically caused great confusion for players because the first versions of *Engine Simulator* were not intended to be used in this way. Recent versions of *Engine Simulator*, however, have solved this problem and made changing engines much easier. Some older community-made engines, however, might be formatted differently and won't work immediately with newer versions. This guide will show you how to solve these issues.

## Step 1 - Navigate to the Community Engine Hub
Follow [this link](https://catalog.engine-sim.parts/) to the *Engine Simulator* community hub where hundreds of engines have been uploaded by players.

## Step 2 - Be Careful Online
There are no *known* security vulnerabilities in *Engine Simulator* and no known ways that someone could inject malicious code or viruses into an engine file. HOWEVER, it is important to always exercise caution online and acknowledge the risks of running any foreign software from a potentially untrustworthy source.

## Step 3 - Choose an Engine and Download It
Download an engine of your choice and place it wherever you like.
![Alt text](assets/screenshot_01.PNG?raw=true)

## Step 4 - Load the Engine in *Engine Simulator*
Press the "Load Script" button in *Engine Simulator*, navigate to the engine you downloaded and open it.

## Step 5 - Debug Common Issues
Sometimes an engine will not load and you'll see "<Error: Check Console>" in the status text. *Engine Simulator* will automatically open the console when this happens. You can navigate between the console and the engine visualizer using the `F5` key or the button to the right of the title.

![Alt text](assets/screenshot_02.PNG?raw=true)

In the screenshot above, the script compiled successfully but *Engine Simulator* is complaining that it's missing a vehicle, engine and transmission. In this case, the fix is easy. First, open the `.mr` file that you downloaded. Search the file for the text `set_engine`. This command tells *Engine Simulator* which engine to simulate. Since it's not present, *Engine Simulator* doesn't know what to simulate.

In the catalog site you may see that the authors of engines have specified instructions for a `main.mr` file. This is the old way of changing engines which is now discouraged. Instead, simply transplant the `main.mr` instructions and put them at the end of the downloaded script.

![Alt text](assets/screenshot_03.PNG?raw=true)

In this case, the original author supplied the three commands needed to set the engine, transmission and vehicle. Moving this exact text to the bottom of the script will solve the issue for this script:

```
set_engine(eng())
set_transmission(trn())
set_vehicle(veh())
```

**However, it is strongly recommended to instead use the following instead:***

```
run(
    engine: eng(),
    transmission: trn(),
    vehicle: veh()
)
```

Reloading the script should then load the engine successfully.

### Engines that use `public node main`
Some newer scripts will have something like this at the bottom:

```
public node main {
    set_engine(Nissan_RB26())
    set_vehicle(Nissan_GTR_R32())
    set_transmission(RB26_transmission())
}
```

In this case, simply adding the following code to the end of the file will work:

```
main()
```

The best way to update this file, however, would be to replace the `main` code above with this instead:

```
run(
    engine: Nissan_RB26(),
    vehicle: Nissan_GTR_R32(),
    transmission: RB26_transmission()
)
```

## Conclusion
Following the steps in this guide should allow you to load most engines in the online catalog. In some cases, engines are so old that the script will not run properly in newer versions. In this case, you'll either need to update the script yourself or run it in an older version of *Engine Simulator*

The next tutorial will teach you how to modify and build engines yourself!

- [Tutorial 3: Running Community Engines](../02_using_community_engines/02_using_community_engines.md)
- [Back to main page](../../README.md)
