dat.fire
===

A simple way to connect your [dat.gui](https://github.com/dataarts/dat.gui) controllers to a [Firebase Realtime Database](https://firebase.google.com/docs/database/).

<img src="https://github.com/googlecreativelab/dat.fire/raw/master/imgs/fbplusdatgui.png" width="800" height="314" />
 
usage 
---
```javascript
// initialize dat.fire with an initialized firebase db
import DatFire from 'dat.fire'
import firebase from 'firebase'
firebase.initializeApp(config)
let datFire = new DatFire(firebase.database())

// create your dat.gui like normal (with or without folders)
let gui = new dat.GUI();
let guiSpeed = gui.add(settings, 'speed', 0, 3).listen();
let guiDieSpeed = gui.add(settings, 'dieSpeed', 0.0005, 0.05).listen();
...

// once all controllers are created, initialize dat.fire
datFire.init(gui)

// or only pass in the controllers you want to connect
datFire.init(gui, [guiSpeed, guiDieSpeed, ...])

// optionally add parameters for further simplicity
datFire.init(gui, null, { 'usePrevNext': true, 'simpleGui': true })
``` 

In that last example, notice that controllers array is null, which functions like the first line and automatically grabs all available controllers from dat.gui.

Once dat.fire has all the controllers, it will use its `property` string as the reference expected in the Firebase Database to handle value changes via a [value event](https://firebase.google.com/docs/database/web/read-and-write#listen_for_value_events). 

Google I/O
---

Check out the full setup at our Experiments Tent at Google I/O this year. All four components were open sourced.
 
 [image from i/o setups]

The Android Experiment using Android Things is located [here](https://github.com/googlecreativelab/things-with-firebase-at-io2017) as well as a fork of The Spirit, a Chrome Experiment implementing dat.fire, located [here](https://github.com/trippedout/The-Spirit/)
