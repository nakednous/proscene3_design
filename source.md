<section id="themes">
	<h2>Themes</h2>
		<p>
			Set your presentation theme: <br>
			<!-- Hacks to swap themes after the page has loaded. Not flexible and only intended for the reveal.js demo deck. -->
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/black.css'); return false;">Black (default)</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/white.css'); return false;">White</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/league.css'); return false;">League</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/sky.css'); return false;">Sky</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/beige.css'); return false;">Beige</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/simple.css'); return false;">Simple</a> <br>
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/serif.css'); return false;">Serif</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/night.css'); return false;">Night</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/moon.css'); return false;">Moon</a> -
			<a href="#" onclick="document.getElementById('theme').setAttribute('href','css/theme/solarized.css'); return false;">Solarized</a>
		</p>
</section>

H:

# Proscene3 Design

Jean Pierre Charalambos

H:

# Index

 1. Goal <!-- .element: class="fragment" data-fragment-index="1"-->
 2. Design<!-- .element: class="fragment" data-fragment-index="2"-->
 3. BIAS<!-- .element: class="fragment" data-fragment-index="3"-->
 4. Dandelion<!-- .element: class="fragment" data-fragment-index="4"-->
 5. Proscene3<!-- .element: class="fragment" data-fragment-index="5"-->
 
H:

## Goal: History

<li class="fragment"> Proscene 1 (processing 1 cycle)
<li class="fragment"> Proscene 2 (processing 2 cycle)
<li class="fragment"> Proscene 3...

V:

## Goal

Provide interactivity to application objects from any input source

in the 'simplest' possible way <!-- .element: class="fragment" data-fragment-index="1"-->

V:

## Goal: Main interaction tasks

Three main interaction tasks (see ['A Survey of Interaction Techniques for Interactive 3D Environments', Jankowski et al](https://hal.inria.fr/hal-00789413/)):

<li class="fragment"> Navigation
<li class="fragment"> Picking and manipulation
<li class="fragment"> Application control

V:

## Goal: Main interaction tasks
### 1. 2D & 3D Navigation

Basic camera types:

<li class="fragment"> Orbit-like methods
<li class="fragment"> First person
<li class="fragment"> Third person

V:

## Goal: Main interaction tasks
### 2. Picking & Manipulation

<li class="fragment"> Picking strategies: from input sources, programmatically
<li class="fragment"> Manipulation: emulate 6 DOF's (Default behavior from multiple _input Sources_)

V:

## Goal: Main interaction tasks
### 3. Application control (custom behaviors)

Post-WIMP interaction styles
<li class="fragment"> Interfaces ???containing at least one interaction technique
not dependent on classical 2D widgets??? [[van Dam]](http://dl.acm.org/citation.cfm?id=253708), such as:
<li class="fragment"> Virtual, mixed and augmented reality
<li class="fragment"> [Tangible interaction](https://en.wikipedia.org/wiki/Tangible_user_interface), ubiquitous and pervasive computing, context-aware computing
<li class="fragment"> Handheld, or mobile interaction
<li class="fragment"> Perceptual and [affective computing](https://en.wikipedia.org/wiki/Affective_computing)
  
N:

WIMP: "window, icon, menu, pointing device"
classical 2D widgets:  menus and icons

V:

## Goal

Provide _interactivity_ to _application objects_ from any _input source_

V:

## Goal
### Interactivitiy

* Default: navigation and picking & manipulation
* Custom

V:

## Goal
### Application Objects

> Provide interactivity to _application objects_ from any _gesture input source_

in the simplest possible way
<!-- .element: class="fragment" data-fragment-index="1"-->

V:

## Goal: Interactivity

Universal interaction tasks:

 1. 2D & 3D viewpoint manipulation <!-- .element: class="fragment" data-fragment-index="1"-->
 2. Picking & Manipulation -> select & interaction <!-- .element: class="fragment" data-fragment-index="2"-->
 3. Application Control -> 'post-'WIMP interaction metaphors <!-- .element: class="fragment" data-fragment-index="3"-->


For a relatively recent survey please refer to: "A Survey of Interaction Techniques for Interactive 3D Environments", Jankowski et al., 2013 - STAR.
<!-- .element: class="fragment" data-fragment-index="4"-->
=======
## Design: API considerations

<li class="fragment"> Simplicity: Separate _application object_ behaviors from _input sources_
<li class="fragment"> Flexibility: Simple default (common) behaviors vs challenging ones

V:

## Design

<li class="fragment"> _Application objects_ -> *Grabbers*
<li class="fragment"> _Input source_ -> *Agents*
<li class="fragment"> Common _event interface_ -> *BogusEvents*

V:

## Goal

It is also about:

<li class="fragment"> Creating academic materials: software + documentation (API-docs + html5 e-book, tutorials & wikis)
<li class="fragment"> Appropiation through collaboration: open-sourcing the materials to encourage hacking them

H:

## Design

<figure>
    <img height='400' src='fig/packages.png' />
    <figcaption>Packages</figcaption>
</figure>

H:

## Bias

<figure>
    <img height='400' src='fig/bias.png' />
    <figcaption>Packages</figcaption>
</figure>

V:

## Bias: Package

> Bogus Input Action Selector 

V:

## Bias: goal

<figure>
    <img height='300' src='fig/arch_5.png' />
    <figcaption>Communication channel</figcaption>
</figure>

V:

<<<<<<< HEAD
## Bias: User gestures

<figure>
    <img height='500' src='fig/arch_4.png' />
    <figcaption>Input sources</figcaption>
</figure>

V:

## Bias: Grabbers

<figure>
    <img height='500' src='fig/arch_3.png' />
    <figcaption>Pickable </figcaption>
</figure>

V:

## BIAS: Grabbers
=======
## BIAS
### Bogus events

Message _interface_ between input sources and application objects

V:

## BIAS
### Bogus events: Types

 * KeyboardEvent <!-- .element: class="fragment" data-fragment-index="1"-->
 * ClickEvent <!-- .element: class="fragment" data-fragment-index="2"-->
 * MotionEvent <!-- .element: class="fragment" data-fragment-index="3"-->
   * DOF1Event
   * DOF2Event
   * DOF3Event
   * DOF6Event

V:

## BIAS
### Bogus events: properties

<li class="fragment"> Every _bogus event_ encapsulates a ```Shortcut```
<li class="fragment"> A ```flushed()``` event encapsulates a gesture termination message
<li class="fragment"> Motion events are ```relative``` or ```absolute``` and they have ```speed``` and ```delay```
<li class="fragment"> Bogus events are _extensible_

V:

## BIAS
### Grabbers

```java
public interface Grabber {
	/**
	 * Defines the rules to set the application object as
	 * an input grabber.
	 */
	boolean checkIfGrabsInput(BogusEvent event);

	/**
	 * Defines how the application object should behave
	 * according to a given BogusEvent, which may hold
	 * a user-defined action.
	 */
	void performInteraction(BogusEvent event);
}
```

V:

<<<<<<< HEAD
## Bias: BogusEvents

<figure>
    <img height='500' src='fig/arch_2.png' />
    <figcaption>Input sources</figcaption>
</figure>

V:

## BIAS: BogusEvents
### Shortcuts

> A gesture identifier

Example: The mouse button + modifier mask when a dragging gesture is taking place
<!-- .element: class="fragment" data-fragment-index="1"-->
=======
## BIAS
### Agents

Collect and reduce input into a _BogusEvent_ in order to:

<li class="fragment"> Update the _Grabber_ (```agent.inputGrabber()```)
<li class="fragment"> Perform an interaction on the ```agent.inputGrabber()```

V:

## BIAS
### Agents


Update the _Grabber_

## BIAS: BogusEvent
### MultiTempi

<li class="fragment"> ```fired()```: event instantiation
<li class="fragment"> ```flushed()```: event termination
<li class="fragment"> ```!fired() && !flushed()```: event execution (default state)

V:

## BIAS: BogusEvent
### Types

_BogusEvent_ instances are of the following types:

 * KeyboardEvent -> 't', 'U', or with modifiers: Shift + 'w'
 <!-- .element: class="fragment" data-fragment-index="1"-->
 * ClickEvent: -> aka "tap", 1,2,...n clicks. Supports modifiers
 <!-- .element: class="fragment" data-fragment-index="2"-->
 * MotionEvent -> kinematics & DOFs, abs/rel, speed
 <!-- .element: class="fragment" data-fragment-index="3"-->
   * DOF1Event
   * DOF2Event
   * DOF3Event
   * DOF6Event

V:

## Bias: Agent
### BogusEvent reduction

<figure>
    <img height='420' src='fig/arch_1a.png' />
    <figcaption>Collect and reduce input into a _BogusEvent_</figcaption>
</figure>
=======
```java
protected Grabber updateTrackedGrabber(BogusEvent event)
```

The ```inputGrabber()``` may be set with ```agent.setDefaultGrabber(Grabber grabber)```

V:

## BIAS
### Agents

Perform an interaction on the ```inputGrabber()```

```java
protected <E extends Enum<E>> boolean handle(BogusEvent event)
```

Two cases arise:
<li class="fragment"> ```!(inputGrabber() instanceof InteractiveGrabber)``` -> agent send the _bogusEvent_ (to the _Grabber_)
<li class="fragment"> ```else```  -> agent send the _bogusEvent_ *and* attach an _action_ (to the _InteractiveGrabber_) using a _Branch_. See _Agent branches_

V:

## Bias: Agent
#### updateTrackedGrabber(): Update the 'inputGrabber()'

<figure>
    <img height='450' src='fig/arch_1.png' />
    <figcaption>grabber.checkIfGrabsInput(event)</figcaption>
</figure>

V:

## Bias: Agent
#### handle(): perform an interaction on the 'inputGrabber()'

<figure>
    <img height='450' src='fig/arch.png' />
    <figcaption>grabber.performInteraction(event)</figcaption>
</figure>

V:

## BIAS: Example
### Part 1: Implementing an agent

```java
protected KeyboardEvent currentEvent;

public void keyEvent(processing.event.KeyEvent e) {
    press = e.getAction() == processing.event.KeyEvent.PRESS;
    release = e.getAction() == processing.event.KeyEvent.RELEASE;
    
    // event reduction Processing -> BogusEvent
    currentEvent = new KeyboardEvent(e.getModifiers(), e.getKey());
    if (press)
      // update only on press
      updateTrackedGrabber(currentEvent);

    // always handle
    handle(release ? currentEvent.flush() : currentEvent.fire());
  }
```

V:

## BIAS: example
### Part 2: Implementing a grabber

```java
public class GrabberObject implements Grabber {
    @Override
    boolean checkIfGrabsInput(BogusEvent event) {
        return withinShapeProjectionArea(event);
    }
    
    @Override
    void performInteraction(BogusEvent event) {
        if ( ( event.shortcut().id() == LEFT ) )
          callback_method(event);
    }
=======
## BIAS
### Agent branches

<li class="fragment"> An agent _branch_ is a collection of _Profiles_ (why NOT a single one?)
<li class="fragment"> A _profile_ is a (_bogusEvent_) _shortcut_ _action_ mapping, i.e., ```public class Profile<K extends Shortcut, A extends Action<?>> implements Copyable```
<li class="fragment"> A _shortcut_ is a _bogusEvent_ mean for invoking an _action_

V:

## BIAS
### Agent branches: Action

```java
public interface Action<E extends Enum<E>> {
	/**
	 * Returns group to global action item mappings.
	 */
	E referenceAction();

	/**
	 * Returns a description of the action.
	 */
	String description();
}
```

V:

## BIAS: Grabber Profile

A [functional programming](https://en.wikipedia.org/wiki/Functional_programming) extension which parses the event in
```grabber.performInteraction(BogusEvent event)```
to define _Shortcut_ to _Method_ bindings. To set it up just override
the _grabber_ ```performInteraction``` method like this:

```java
@Override
public void performInteraction(BogusEvent event) {
    profile.handle(event);
}
```
<!-- .element: class="fragment" data-fragment-index="1"-->
=======
## BIAS
### Agent branches: InteractiveGrabbers

```java
public interface InteractiveGrabber<E extends Enum<E>> extends Grabber {
	public void setAction(Action<E> action);
	public Action<E> action();
}
```
>>>>>>> fc44622e34eefd5767bbb5ea5f5bab28046b2fb1

V:

## BIAS
<<<<<<< HEAD
### Grabbers: Profile

Profiles allow the following simple dialect:

```java
grabber.setMotionBinding(LEFT, "callback_method");
```
<!-- .element: class="fragment" data-fragment-index="1"-->

```java
grabber.setKeyBinding('x', "callback_method");
```
<!-- .element: class="fragment" data-fragment-index="2"-->

```java
grabber.setKeyBinding(SHIFT, 'y', "callback_method");
```
<!-- .element: class="fragment" data-fragment-index="3"-->

```java
grabber.setClickBinding(RIGHT, '2', "callback_method");
```
<!-- .element: class="fragment" data-fragment-index="4"-->

V:

## BIAS: Conclusions

<li class="fragment"> Target audience: advanced programmers with (TODO name scenarios here with references)
<li class="fragment"> Multi-language (java + android + js) = Java-based implementation + single-threaded + No-dependencies
<li class="fragment"> Which means it can easily be plugged into any third-party visual computing application
<li class="fragment"> A wide scope of interactive applications
<li class="fragment"> Simple to very complex input setups, even allowing concurrency of input events on application objects
<li class="fragment"> Software maintenance and extensibility, such as when adding new hardware and/or application user-defined actions
<li class="fragment"> TODO: pending reference to bias wiki
=======
### Agent branches: Multi-tempi Actions

Idea is quite simple

Multiple tempi actions (such as press-drag-release with a mouse) may be identified from
a Grabber by analysing the flow of events respect to an initAction, as follows:

V:

## BIAS
### Agent branches: Multi-tempi Actions

<li class="fragment"> ```initAction(BogusEvent)``` (1st tempi): sets the ```initAction```, called when ```initAction == null```
<li class="fragment"> ```execAction(BogusEvent)``` (2nd tempi): continues action execution, called when ```initAction == action()```
<li class="fragment"> ```flushAction(BogusEvent)``` (3rd tempi): ends action, called when ```BogusEvent.flushed()``` is true or when ```initAction != action()```

H:

## Dandelion

<figure>
    <img height='400' src='fig/dandelion.png' />
    <figcaption>Packages</figcaption>
</figure>

V:

## Dandelion: Goal

> Interactivitiy to *frames* (coordinate systems)
=======
<li class="fragment"> Default *agents*
<li class="fragment"> Interactivitiy to *frames* ( _grabber_ coordinate systems)

V:

## Dandelion
### Packages

<li class="fragment"> *dandelion.geom* -> _Vec_, _Quat_, _Mat_ and _Frame_ (_Quat_ + _Vec_)
=======
<li class="fragment"> *dandelion.branch* -> _InteractiveFrame_ and _InteractiveAvatarFrame_; _MotionAgent_ and _KeyboardAgent_
<li class="fragment"> *dandelion.geom* -> _Vec_, _Quat_, _Mat_ and _Frame_ (_Quat_ + _Vec_)
<li class="fragment"> *dandelion.core* -> _Eye_, _GrabberFrame_

<li class="fragment"> *dandelion.constraint* -> Apply constraints to _Frames_ to limit their motion
<li class="fragment"> *dandelion.core* -> _GenericFrame_, _KeyFrameInterpolator_, _Eye_, and _AbstractScene_

V:

## Dandelion
### Frame: Hierarchy

```sh
 world
  ^
  |\
  | \  
  f1 eye
  ^   ^
  |\   \
  | \   \
  f2 f3  f5
  ^
  |
  |
  f4
```

```java
  frame.setReferenceFrame(parent);
```

V:

## Dandelion
### Frame: Hierarchy

```java
  Frame frame = new Frame();
  scene.pushModelView();
  scene.applyModelView(frame.matrix());
  // Draw your object here, in the local fr coordinate system.
  scene.popModelView();
```

V:

## Dandelion
### GenericFrame

> A Frame Grabber (frame that implements the Grabber interface)

<li class="fragment"> Frames that are pickable and interactive
<li class="fragment"> A frame is *generic* in that it can belong either to an object or to the Eye
<li class="fragment"> Scene-graph: Allows top/down traversals of the frame hierarchy
<li class="fragment"> third-person cam: A gFrame can be followed by another camera

N:

For the scenegraph we need to keep references to frame children. We did it internally, preserving the same API (setReferenceFrame does it all)

V:

## Dandelion
### KeyFrameInterpolator

<li class="fragment"> Interpolation paths [Catmull Rom](https://en.wikipedia.org/wiki/Cubic_Hermite_spline#Catmull.E2.80.93Rom_spline)

TODO: video here

V:

## Dandelion
### Eye

<li class="fragment"> 2D (Window) & 3D (Camera)
<li class="fragment"> Back-face culling
<li class="fragment"> View-frustum made easy, while targetting the [z-Buffer precision](https://www.opengl.org/wiki/Depth_Buffer_Precision)

V:

## Dandelion
### AbstractScene: high-level scene-graph API

High-level secne handler which manages:

<li class="fragment"> Visual hints
<li class="fragment"> Traversal algorithm: 
<li class="fragment"> Frame-hierarchy
<li class="fragment"> BIAS agents

V:

## Dandelion: Conclusions

<li class="fragment"> Target audience: programmers which want to build upon a scenegraph foundation
<li class="fragment"> Multi-language (java + android + js) = Java-based implementation + single-threaded + No-dependencies simple
and coherent scene-graph API
<li class="fragment"> Those of BIAS
<li class="fragment"> It can easily be plugged into any third-party visual computing application
<li class="fragment"> TODO: pending reference to bias wiki

H:

## Proscene3

<figure>
    <img height='400' src='fig/packages.png' />
    <figcaption>Packages</figcaption>
</figure>

V:

## Proscene3

<li class="fragment"> Bridge between Dandelion and [Processing3](http://processing.org)
<li class="fragment"> Seamless thorough integration between the two
<li class="fragment"> Takes full advantage of Processing concise API and its advanced-rendering capabilities (TODO: videos, references here)

V:

## Proscene3
### InteractiveFrame

* _InteractiveFrame_ -> _GenericFrame_ [PShape](https://processing.org/reference/PShape.html) wrapper implementing ```checkIfGrabsInput(event)``` using a [picking buffer](http://content.gpwiki.org/index.php/OpenGL_Selection_Using_Unique_Color_IDs)
<figure>
    <img height='300' src='fig/picking_buffer.png' />
    <figcaption>Picking buffer</figcaption>
</figure>

V:

<<<<<<< HEAD
## Dandelion
### AbstractScene: high-level scene-graph API

<li class="fragment"> Default rendering of shapes not already present on the Processing API, such hollow cylinder or cone
<li class="fragment"> Traversal algorithm: ```scene.drawFrames()```
<li class="fragment"> InterativeFrames can be projected onto an arbritary number of (off-screen) graphics buffer

V:

## Proscene3
### Envisaged interactive scenarios: Custom Appearance

```java
  public void setup() {
    frame = new InteractiveFrame(scene, createShape(SPHERE, 40));
  }
```

V:

## Proscene3
### Envisaged interactive scenarios: Custom Appearance

```java
  public void setup() {
    frame = new InteractiveFrame(scene, this, "boxDrawing");
  }
  
  public void boxDrawing(PGraphics pg) {
    pg.box(30);
  }
```

V:

## Proscene3
### Envisaged interactive scenarios: Custom Actions

```java
  public void setup() {
    frame.setMotionBinding(LEFT, "translate");
  }
```

V:

## Proscene3
### Envisaged interactive scenarios: Custom Actions

```java
  public void setup() {
    frame.setMotionBinding(this, LEFT, "boxCustomMotion");
  }
  
  public void boxCustomMotion(InteractiveFrame frame, MotionEvent event) {
    frame.screenRotate(event);
  }
```

V:

## Proscene3
### Envisaged interactive scenarios: Examples

[2D image deformation](https://github.com/sechaparroc/Deformation) and [3D mesh deformation](https://github.com/sechaparroc/Deformation3D)
=======
## Proscene3: examples

Navigation: All examples

* Orbit-like methods: all examples using a mouse
* First person: [first person](https://github.com/remixlab/proscene/tree/master/examples/Eye/FirstPersonCamera)
* Third person: [third person](https://github.com/remixlab/proscene/tree/master/examples/Eye/ThirdPersonCamera) and [flock](https://github.com/remixlab/proscene/tree/master/examples/Timing/Flock)

V:

<<<<<<< HEAD
## Proscene3
### Envisaged interactive scenarios: Interactive dance performance

Stages:

1. Gesture recognition
2. Custom action set on the _InteractiveFrame_ defining its motion (most likely) using Inverse Kinematics
3. Shading

Note: Custom bogus events?
=======
## Proscene3: examples

Picking and manipulation: all examples with _Frames_

//TODO: shader chaining, scene-graph

V:

## Proscene3: Conclusions

<li class="fragment"> Target audience: that of [Processing](https://processing.org/)
<li class="fragment"> Multi-language (java + android + js) = Java-based implementation + single-threaded + No-dependencies
<li class="fragment"> Single and multi-threaded timers
<li class="fragment"> Those of Dandelion & BIAS, but already pluged in into Processing

H:

## Roadmap

<li class="fragment"> Short term: Release _Proscene3_ -> JS and Android port
<li class="fragment"> Middle term: _Proscene3_ cycle -> Collaborations (as with most cycles)
<li class="fragment"> February 2017: Release of the curse materials: software + documentation
=======
## Proscene3: examples

Application control: [deformation](https://github.com/nakednous/Deformation)
