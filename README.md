# ALL CREDIT TOWARDS **Andy Coenen** FOR CREATING SCATTERGL

Since this is a fork with minor modifications, if the creators would like
for this to be taken down from npm, please make an issue on the [repo](https://github.com/xnought/scatter-gl). This is also where you can see the modifications. I only had this published to npm for ease of installation when I use this modified package for projects. I did not write all of this code, I just added the a few methods and modified callbacks to call more often.

## THIS IS FORKED FROM [ScatterGL from Google PAIR](https://github.com/PAIR-code/scatter-gl)

I forked this in order to modify the ScatterGL class to include 2 more methods.
One is a callback that is given on creation of ScatterGL called `onCameraDrag` (similar to `onCameraMove`, but called every single position
instead of just once.
) and `setCameraPositionAndTarget(position: Point3D, target: Point3D)` which is a method that can be called to set a new position and target.

### Reasoning

This was used to sync up multiple camera positions from moving just one ScatterGL plot.

## Examples

#### Basic use

```javascript
// where `points` is an array of 2 or 3-dimensional points as number arrays.
const dataset = new ScatterGL.Dataset(points);
const scatterGL = new ScatterGL(containerElement);
scatterGL.render(dataset);
```

#### Parameters

The `ScatterGL` constructor can accept a number of parameters via a `ScatterGLParams` object:

| Parameter           | Type                                                                               | Description                                                                                                                   | default                                                                                                       |
| ------------------- | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `onCameraDrag`      | `(cameraPosition: THREE.Vector3, cameraTarget: THREE.Vector3) => void`             | A callback invoked the camera moves due to user interaction. Will be run every single new position when drag camera position. |                                                                                                               |
| `camera`            | `Camera`                                                                           | An object containing default parameters for the camera                                                                        | Camera params object (`zoom: number`, `target: Point3D`, and `position: Point3D`)                             |
| `onClick`           | `(point: Point \| null) => void`                                                   | A callback invoked when clicking on a point or elsewhere                                                                      |                                                                                                               |
| `onHover`           | `(point: Point \| null) => void`                                                   | A callback invoked when hovering over a point                                                                                 |                                                                                                               |
| `onSelect`          | `(points: Point[]) => void`                                                        | A callback invoked when a point or points are selected                                                                        |                                                                                                               |
| `onCameraMove`      | `(cameraPosition: THREE.Vector3, cameraTarget: THREE.Vector3) => void`             | A callback invoked the camera moves due to user interaction.                                                                  |                                                                                                               |
| `pointColorer`      | `(index: number, selectedIndices: Set<number>, hoverIndex: number|null) => string` | A function to determine the color of points                                                                                   |                                                                                                               |
| `renderMode`        | `RenderMode`                                                                       | The render mode to display points, one of `RenderMode.POINT`, `RenderMode.SPRITE`, or `RenderMode.TEXT`                       | `RenderMode.POINT`                                                                                            |
| `showLabelsOnHover` | `boolean`                                                                          | Whether or not to render label text on hover                                                                                  | `true`                                                                                                        |
| `selectEnabled`     | `boolean`                                                                          | `true`                                                                                                                        | Whether or not a user can select points by clicking                                                           |
| `styles`            | `Styles`                                                                           | An object containing style parameters to override the default options                                                         |                                                                                                               |
| `rotateOnStart`     | `boolean`                                                                          | Whether or not the renderer automatically rotates until interaction                                                           | `true`                                                                                                        |
| `orbitControls`     | `OrbitControlParams`                                                               | An object containing default parameters for the orbit controls                                                                | Orbit Controls params object (`zoomSpeed: number`, `autoRotateSpeed: number`, and `mouseRotateSpeed: number`) |

#### ScatterGL methods

| Method                                                           | Description                                                |
| ---------------------------------------------------------------- | ---------------------------------------------------------- |
| `setCameraPositionAndTarget(position: Point3D, target: Point3D)` | Sets the camera position and target                        |
| `isOrbiting()`                                                   | Returns whether the orbit animation is currently on        |
| `render(dataset: Dataset)`                                       | Initializes and renders a dataset to the container element |
| `resize()`                                                       | Updates the render size based on the container element     |
| `select(pointIndices: number[])`                                 | Selects points by index                                    |
| `setPanMode()`                                                   | Sets interaction mode to 'pan'                             |
| `setPointColorer(pointColorer: PointColorer)`                    | Sets a function to determine colors                        |
| `setHoverPointIndex()`                                           | Sets the hovered point                                     |
| `setPointRenderMode()`                                           | Sets point render mode                                     |
| `setRenderMode(renderMode: RenderMode)`                          | Sets a specific render mode                                |
| `setSelectMode()`                                                | Sets interaction mode to 'select'                          |
| `setSequences(sequences: Sequence[])`                            | Sets sequences with which to render polylines              |
| `setSpriteRenderMode()`                                          | Sets sprite render mode                                    |
| `setTextRenderMode()`                                            | Sets text render mode                                      |
| `updateDataset(dataset: Dataset)`                                | Updates the dataset                                        |
| `startOrbitAnimation()`                                          | Begin rotating until an interaction                        |
| `stopOrbitAnimation()`                                           | Stops automatic rotation                                   |

## Advanced usage

See the [demo app](./demo/index.ts) for examples of interaction handling, spritesheet rendering, and point coloring.

## Styling

You can provide an object in the form of [`Styles`](./src/styles.ts) via the `styles` parameter of the `ScatterGLParams` object.

## Development

```bash
yarn
yarn demo
```

**This is not an officially supported Google product**
