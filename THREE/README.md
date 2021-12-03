# Three JS Helpers

## Useful Links
* GTLF Files - https://sketchfab.com/tags/gltf
* Three JS - https://threejs.org/


## Top Level
* These are top level functions that will get your project up and running

### Init() Function
```js
// Set up global scope
let container;
let camera;
let renderer;
let scene;
// Add any new global objects to the scope
let object1;
let object2;

const init = () => {
  // Put your containers camera renderer and scene in here
  animate();
}

const animate = () => {
  // Put your animations here
}

init();
```

### Container
* Use vanilla JS to target an HTML element `container = document.querySelector("body");`

### Scene
* Initiate Three JS using `scene = new THREE.Scene();`
* Anything you create needs to be added to the scene

### Camera
```js
const fov = 35; // Angle of how much the camera sees
const aspect = container.clientWidth / container.clientHeight; // Sets the size of the camera view
const near = 0.1; // How close up things can be before they cut off
const far = 1000; // How far you can see

//Camera setup
camera = new THREE.PerspectiveCamera(fov, aspect, near, far);
camera.position.set(0, 5, 30);
```

### Renderer
* https://threejs.org/docs/#api/en/renderers/WebGLRenderer
```js
renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
renderer.setSize(container.clientWidth, container.clientHeight);
renderer.setPixelRatio(window.devicePixelRatio);

container.appendChild(renderer.domElement);
renderer.render(scene, camera);
```

### Animation Loop
```js
const animate = () => {
  requestAnimationFrame(animate);
  object1.rotation.z += 0.005; // Rotate speed
  renderer.render(scene, camera);
}
```

### X Y Z Axis
* Use the following to help you develop `scene.add(new THREE.AxesHelper(500))` where 500 is the length of these axis
* **X** - The 2D plane in front of you from left and right
* **Y** - The 2D plane in front of you from up and down
* **Z** - The 3rd dimension plane (depth) in front of you far and close


## Common Functions
* Useful functions for projects

### Shapes
* Rendering shapes

#### Cube
* https://threejs.org/docs/#api/en/geometries/BoxGeometry
```js
geometryCube = new THREE.BoxGeometry();
materialCube = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
cube = new THREE.Mesh( geometryCube, materialCube );
scene.add(cube);
```

#### Sphere
* https://threejs.org/docs/#api/en/geometries/SphereGeometry
```js
geometrySphere = new THREE.SphereGeometry();
materialSphere = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
sphere = new THREE.Mesh( geometrySphere, materialSphere );
scene.add(sphere);
```

### Lighting
* Rendering lights in various ways

#### Hemisphere Light
* A general light like the sun
* https://threejs.org/docs/#api/en/lights/HemisphereLight
```js
hemiLight = new THREE.HemisphereLight( 0xffeeb1, 0x080820, 8 );
scene.add(hemiLight);
````

#### Spotlight
* A light source
* https://threejs.org/docs/#api/en/lights/SpotLight
```js
spotlight = new THREE.SpotLight( 0xffeeb1, 4 );
spotlight.castShadow = true;
scene.add(spotlight);


const animate = () => {
  spotlight.position.set(
    camera.position.x + 10,
    camera.position.y + 10,
    camera.position.z + 10,
  )
}
```

### Loaders
* Loading in files

#### GLTF Loader 
* Requires `GLTFLoader.js` which can be found in the three js download file `/examples/js/loaders/GLTFLoader.js`
* If you use a loader, make sure you run `animate()` once the item has loaded

```js
loader = new THREE.GLTFLoader();
loader.load("./path-to/file.gltf", data => {
  scene.add(data.scene);
  object1 = data.scene.children[0]; // Save object
  animate(); // call the animate function once it's loaded
});
```

### Controls
* Mouse / keyboard controls

#### First Person Controls
* Requires `FirstPersonControls.js` which can be found in the three js download file `/examples/js/controls/FirstPersonControls.js`
* Tips below so that the character (first person control) you control can't fly or go underground see `if ( firstPersonControls.object.position.y < character.height - 0.1 )`

```js
// Remember outside of the init() function set clock and character
const character = { height: 1.3 };

firstPersonControls = new THREE.FirstPersonControls(camera, renderer.domElement)
firstPersonControls.lookAt(new THREE.Vector3())
firstPersonControls.lookSpeed = 0.05;
firstPersonControls.movementSpeed = 10;
firstPersonControls.heightCoef = 5; // When you get mouse near the edge of screen how much it speeds up by

firstPersonControls.lookVertical = true;
firstPersonControls.constrainVertical = true;
firstPersonControls.verticalMin = 1.0;
firstPersonControls.verticalMax = 2.0;

clock = new THREE.Clock();

const animate = () => {
  requestAnimationFrame(animate);
  var delta = clock.getDelta();

  if ( firstPersonControls.object.position.y < character.height - 0.1 ) firstPersonControls.object.position.y = character.height - 0.1;
  if ( firstPersonControls.object.position.y > character.height + 0.1 ) firstPersonControls.object.position.y = character.height + 0.1;

  firstPersonControls.update(delta); // Delta required to know how long it was since previous render
  renderer.render( scene, camera );
};
```

#### Orbit Controls
* Allow you to move the scene with your mouse controls e.g. drag scene, zoom etc.
* Requires `OrbitControls.js` which can be found in the three js download file `/examples/js/controls/OrbitControls.js`
* NB - no need to add it to the scene

```js
controls = new THREE.OrbitControls(camera, renderer.domElement)
```

### Animation

#### Pivot Point
* To create a pivot point 
```js
pivotPoint = new THREE.Object3D(); // || pivotPoint = new THREE.Group(); (this works too)
pivotPoint.add(sphere); // A sphere to replicate the position of the light
pivotPoint.add(light); // e.g. Spotlight
```

* Set center of the pivot point and link to object (and scene indirectly as long as object has been added to scene)
```js
object1.add(pivotPoint);
```
* To set the center of the pivot point
```js
const animate = () => {
  requestAnimationFrame(animate);
  object1.rotation.z += 0.005;
  pivotPoint.rotation.z -= 0.05; // The pivot point is fixed to Object 1 so will rotate with it. In this example we rotate the opposite way at same rate to make it appear fixed
  renderer.render(scene, camera);
}
```

### Position
* Get the position of something (if it is moving put in animate loop)

#### Get World Position
* https://threejs.org/docs/#api/en/core/Object3D.getWorldPosition
* In the example below we create a sphere and then assign a variable for it's position in 3d space

```js
geometrySphere = new THREE.SphereBufferGeometry( 1, 32, 32 );
materialSphere = new THREE.MeshBasicMaterial( { color: 0xFFFFE0 } );
sphere = new THREE.Mesh( geometrySphere, materialSphere );
sphere.position.set(5, 5, 5);
scene.add(sphere);

// Important bits
positionSphere = new THREE.Vector3(); // Required for a 3d position 
sphere.getWorldPosition(positionSphere) // Without setting the target of Vector3() it works but you get an error
```

### Helpful Functions
* Other functions that are useful to projects

#### Window Resize
* On window resize
```js
const onWindowResize = () => {
  camera.aspect = container.clientWidth / container.clientHeight;
  camera.updateProjectionMatrix();

  renderer.setSize(container.clientWidth, container.clientHeight);
}

window.addEventListener("resize", onWindowResize);
```