# Build Your Own Engine From Scratch

This tutorial will teach you how to build an engine from scratch using *Engine Simulator's* scripting interface.

## Prerequisites
### 1. Download and Install VS Code
If you don't already have VS Code installed, you can do so [here](https://code.visualstudio.com/download). You could use any text editor for this but VS Code is recommended if you want syntax highlighting.

### 2. Install the Piranha Syntax Highlighting Plugin
Open VS Code and click on "View" then "Extensions". In the search bar, search for "Piranha".

![Alt text](assets/screenshot_01.PNG?raw=true)

Click on the search result and install the extension.

![Alt text](assets/screenshot_02.PNG?raw=true)

Once the extension is installed, `.mr` files should be colored in VS Code.

![Alt text](assets/screenshot_03.PNG?raw=true)

## 1 - Setting up the Script
1. Create a new file called `tutorial-engine.mr`. It can be called whatever you want by the `.mr` extension must be present
2. Open the file in VS Code (or the text editor of your choice)
3. The first step is to include the following line at the top of the file, which will import everything needed from the *Engine Simulator* library.

```
import "engine_sim.mr"
```

4. Next we need to define an engine. To make organization a bit easier, we will create this engine inside a *node*. A node is a logical unit of code within the Piranha programming language. This can be done with the following code:

```
public node my_engine {
    alias output __out: engine;

    engine engine(
        name: "My Engine"
    )
}
```

Line by line, this is what the code does:
- Line 1 - creates a new node type called `my_engine`
- Line 2 - the main output of this node is going to be the engine node defined below
- Line 3 - empty
- Line 4 - create an `engine` node. This is a node-type that is built into *Engine Simulator* and signifies a common piston engine
- Line 5 - the name of the engine
- Line 6 - closing bracket
- Line 7 - closing brace

5. Tell *Engine Simulator* that this is the engine we want to simulate. To do this, add the following code at the bottom of the file:

```
run(
    engine: my_engine()
)
```

The full script should look like this at this point:

```
import "engine_sim.mr"

public node my_engine {
    alias output __out: engine;

    engine engine(
        name: "My Engine"
    )
}

run(
    engine: my_engine()
)
```

6. Let's try running this script now by pressing the "Load Script" button in *Engine Simulator*.

You should see this in the console:
![Alt text](assets/screenshot_04.PNG?raw=true)

Our script compiled successfully but *Engine Simulator* correctly pointed out that our engine does not have any crankshafts and is therefore invalid. Everything looks fine so far, we just need to continue building our engine.

## 2 - Creating a Crankshaft

1. Specifying engine measurements is much easier with standard units. To use units, add the following line before line 3:

```
units units()
```

2. Next it'll help with our code organization to specify a list of engine parameters. To do that, add the following code before line 9:

```
// Engine parameters
label stroke(86.0 * units.mm)
```

The `label` node is simply a way to give a name to a value. In this case, we are saving the value of 86 mm in a node called `stroke` for use later.

2. Now, it's time to create the crankshaft. The two most important parameters that define the crankshaft are the `throw` and `tdc` position. TDC stands for top-dead-center which is the point at which the piston is at the top of the compression stroke. We'll discuss how this is set in more detail later. Add the following code after the `engine` node:

```
crankshaft crankshaft(
    throw: stroke / 2,
    tdc: 90 * units.deg
)
```

This code creates a new crankshaft object called `crankshaft` with a *throw* of the engine's stroke divided by 2 and `tdc` point of 90 degrees. A crankshaft's "throw" is the distance between the center of the crankshaft to the center of it's rod journals (also called crank-pins).

3. The final step is to add the new crankshaft to the engine using the following code placed underneath the `crankshaft` code earlier:

```
engine.add_crankshaft(crankshaft)
```

By this point, the entire script should look like this:

```
import "engine_sim.mr"

units units()

public node my_engine {
    alias output __out: engine;

    // Engine parameters
    label stroke(86.0 * units.mm)

    engine engine(
        name: "My Engine"
    )

    crankshaft crankshaft(
        throw: stroke / 2,
        tdc: 90 * units.deg
    )

    engine.add_crankshaft(crankshaft)
}

run(
    engine: my_engine()
)
```
