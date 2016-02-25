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
 6. Roadmap<!-- .element: class="fragment" data-fragment-index="6"-->
 
H:

## Goal

Provide interactivity to _application objects_ from any _input source_

H:

## Design

<li class="fragment"> _Application bjects_ -> *Grabbers*
<li class="fragment"> _Input source_ -> *Agents*

V:

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

## Bias

<figure>
    <img height='400' src='fig/architecture.png' />
    <figcaption>Architecture</figcaption>
</figure>

V:

## BIAS
### BogusEvents

V:

## BIAS
### BogusEvents

_BogusEvents_ are of the following types:

 * KeyboardEvent <!-- .element: class="fragment" data-fragment-index="1"-->
 * ClickEvent <!-- .element: class="fragment" data-fragment-index="2"-->
 * MotionEvent <!-- .element: class="fragment" data-fragment-index="3"-->
   * DOF1Event
   * DOF2Event
   * DOF3Event
   * DOF6Event
   
V:

## BIAS
### BogusEvents: Shortcuts



V:

## BIAS
### BogusEvents: Multi-tempi



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

## BIAS
### Grabbers: example

```java
public class CustomGrabberFrame implements Grabber {
    @Override
    boolean checkIfGrabsInput(BogusEvent event) {
        return withinShapeProjectionArea(event);
    }
    
    @Override
    void performInteraction(BogusEvent event) {
        if ( ( event.shortcut().id() == LEFT ) )
          callback_method(event);
    }
}
```

V:

## BIAS
### Grabbers: Profile

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

V:

## BIAS
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

## BIAS
### Grabbers: Profile


```java
public void performInteraction(BogusEvent event) {
    profile.handle(event);
}
```

V:

## BIAS
### Agents

Collect and reduce input into a _BogusEvent_ in order to:

<li class="fragment"> Update the _Grabber_ (```agent.inputGrabber()```)
<li class="fragment"> Perform an interaction on the ```agent.inputGrabber()```

V:

## BIAS
### Agents

Update the _Grabber_

```java
protected Grabber updateTrackedGrabber(BogusEvent event)
```

The ```inputGrabber()``` may be set with ```agent.setDefaultGrabber(Grabber grabber)```

V:

## BIAS
### Agents

Perform an interaction on the ```inputGrabber()```

```java
protected boolean handle(BogusEvent event)
```

V:

## BIAS
### Agents: a KeyAgent example

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

## BIAS
### InputHandler



H:

## Dandelion

<figure>
    <img height='400' src='fig/dandelion.png' />
    <figcaption>Packages</figcaption>
</figure>

V:

## Dandelion

<li class="fragment"> Default *agents*
<li class="fragment"> Interactivitiy to *frames* (coordinate system _grabbers_)

V:

## Dandelion
### Packages

<li class="fragment"> *dandelion.agent* -> _MotionAgent_ and _KeyboardAgent_
<li class="fragment"> *dandelion.geom* -> _Vec_, _Quat_, _Mat_ and _Frame_ (_Quat_ + _Vec_)
<li class="fragment"> *dandelion.core* -> _Eye_, _GrabberFrame_, _InteractiveFrame_ and _InteractiveAvatarFrame_
<li class="fragment"> *dandelion.constraint* -> Apply constraints to _Frames_ to limit their motion

V:

## Dandelion

<figure>
    <img height='400' src='fig/iAvatar.png' />
    <figcaption>Frame hierarchy</figcaption>
</figure>

H:

## Proscene3

<figure>
    <img height='400' src='fig/packages.png' />
    <figcaption>Packages</figcaption>
</figure>

V:

## Proscene3

* Bridge between Dandelion and [Processing3](http://processing.org)
* _Models_ -> _Grabber_ [PShape](https://processing.org/reference/PShape.html) wrapper implementing ```checkIfGrabsInput(event)``` using a [picking buffer](http://content.gpwiki.org/index.php/OpenGL_Selection_Using_Unique_Color_IDs)

<figure>
    <img height='300' src='fig/picking_buffer.png' />
    <figcaption>Picking buffer</figcaption>
</figure>

V:

## Proscene3

<figure>
    <img height='250' src='fig/iModelObject.png' />
    <figcaption>InteractiveModelObject hierarchy</figcaption>
</figure>

V:

## Proscene3

<figure>
    <img height='400' src='fig/iModelFrame.png' />
    <figcaption>InteractiveModelFrame hierarchy</figcaption>
</figure>

V:

## Proscene3
### Envisaged interactive scenarios: Custom Grabbers

Declare some _grabbers_ and override:

1. public boolean checkIfGrabsInput(event)
2. public void performInteraction(event)

Check the [MouseGrabbers](https://github.com/remixlab/proscene/tree/3.0/examples/Basics/MouseGrabbers) example

V:

## Proscene3
### Envisaged interactive scenarios: Custom GrabberFrames

Everything in Dandelion is _GrabberFrame!_. There's no difference between eyeFrame and iFrame what so ever as it was in Proscene2.

For instance implement custom _InteractiveFrames_, i.e., derive from _GrabberFrame_ and parameterise your custom _iFrame_ using a custom _action_ set

Some examples coming soon!

V:

## Proscene3
### Envisaged interactive scenarios: InteractiveModelFrames

[2D image deformation](https://github.com/sechaparroc/Deformation) and [3D mesh deformation](https://github.com/sechaparroc/Deformation3D)

<figure>
    <img height='300' src='fig/image_deformation.png' />
</figure>

Currently being ported to Android

V:

## Proscene3
### Envisaged interactive scenarios: InteractiveModelObject

Interactive dance performance using _InteractiveModelObject_

Stages:

1. Gesture recognition
2. Custom action set on the _InteractiveModelObject_ defining its motion (most likely) using Inverse Kinematics
3. Shading

Note: Custom bogus events?

V:

## Proscene3
### Envisaged interactive scenarios: other customizations

* [GrabberObjects](https://github.com/remixlab/proscene-experiments/blob/master/Interaction/ActionGrabbers/Tutorial2/Tutorial2.pde)
* [InteractiveGrabberObjects](https://github.com/remixlab/proscene-experiments/tree/master/Interaction/ActionGrabbers/Tutorial3)
* [GrabberModelFrames](https://github.com/remixlab/proscene-experiments/blob/master/Interaction/CustomModels/Tutorial0/Tutorial0.pde)
* [interacitveModelObjects](https://github.com/remixlab/proscene-experiments/blob/master/Interaction/CustomModels/Tutorial3/Tutorial3.pde)

H:

## Roadmap

<li class="fragment"> Short term: _Alpha3_ -> Support Processing3-a7, Android port
<li class="fragment"> Middle term: _Beta_ cycle -> API docs, comprehensive set of examples, journal paper
<li class="fragment"> May 2015: Release
