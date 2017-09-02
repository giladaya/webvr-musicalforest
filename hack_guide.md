# Hack Guide
How to change what you want in the experience

## Change sounds
Each shape has a 'tone' which is taken from a set of 6 available sounds for this shape.  
To change the sounds for a shape:
1. Create a folder with the audio files (preferably in mp3 + ogg + wav formats) under `/static/audio` and number the files from 0 to 5.
2. Replace the `name` in one of the entries in `Instruments` array in `/js/core/instruments.js` to the name of the new folder.

## Change BG Colors
Easiest to search for the hex color code of the sky in all `/js` and cahnge all of them.  
These are at least necessary:
- `/js/ascene.js`
    - `a-scene.fog.color`
    - `a-entity#gaze-floor.material.color`
- `/js/splash.js`
    - `floorStatic.material.color`

## Change BG trees object
There are 3 models used for the BG trees.  
They are loaded and used in `/js/components/background-objects.js`.
To use a different 3D model, add it to `/static/models` and add its name to `this.treeObjs` in `/js/components/background-objects.js`.  
Note that the shadows are originally simple `PlaneGeometry` objects that are placed in the right location. They should be removed or treated separately.  

## Change instrument shapes
This needs more research to enable loading geometry / materials from files.  
The original shapes are box, ball and tetrahedron. The first two are primitives, but the tetrahedron is defined in code and used in `/js/notes/note-head-tetra.js`.  
All shapes are defined as aframe components in `/js/components/ball.js` which delegates behavior to a child `note` instance: `/js/notes/note.js`.
