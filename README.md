## Visual Computing Slides -- Proscene3_Design

[Proscene3](https://github.com/remixlab/proscene/) design, implementation and future.

Powered by [reveal](https://github.com/hakimel/reveal.js).

Made possible thanks to... 

<!--- a long list of students and links to their pages. To come ;) -->

## Installation

 ```sh
 $ git clone https://github.com/VisualComputing/proscene3_design.git
 $ cd proscene3_design
 $ git checkout gh-pages
 ```

## Folder Structure

    |-- css/
    |-- js/
    |-- plugin/
    |-- lib/
    |-- fig/
    |-- sketches/
    |-- index.html
    |-- source.md
    
Refer to the [reveal folder structure](https://github.com/hakimel/reveal.js#folder-structure) for more details, and to the *Setup* below.

## Setup

External markdown and speaker notes, require that presentations run from a local web server. The following instructions will set up such a server as well as all of the development tasks needed to make edits to the slides source code.

1. Install [Node.js](http://nodejs.org/)

2. Install [Grunt](http://gruntjs.com/getting-started#installing-the-cli)

3. Install dependencies (you must be already on the presentation folder, otherwise ```$ cd proscene3_design```)

 ```sh
 $ npm install
 ```

4. Edit the presentation contents using [markdown](http://daringfireball.net/projects/markdown/) in the `source.md`, adding figures to the `fig/` folder and [p5.js skectches](http://p5js.org/) to the `skectches/` folder (detailed instructions below) as needed.

5. Serve the presentation and monitor source files for changes

 ```sh
 $ grunt serve
 ```

6. Open <http://localhost:8000> to view your presentation

 You can change the port by using `grunt serve --port 8001`.

<!---

7. Update to upstream

 ```sh
 $ git remote add reveal.js https://github.com/hakimel/reveal.js.git
 $ git pull reveal.js master
 ```
-->

## [p5.js](http://p5js.org/) sketches

1. Create your js sketch in the ```sketches``` folder, e.g.,


 ```sh
 $ touch sketches/mysketch.js
 ```
 
2. Define a canvas _id_ (e.g., ```mysketch_id```) within your _mysketch.js_ `setup` function:

 ```javascript
 function setup() {
    var myCanvas = createCanvas(400, 400);
    myCanvas.parent('mysketch_id');
 }
 ```

3. Include your sketch as a script in the ```index.html```, e.g., ```<script src="sketches/mysketch.js"></script>```

4. Locate your sketch in the ```source.md``` at the place you want it to be, using the _id_: defined in step *2*, e.g., ```<div id='mysketch_id'></div>```
