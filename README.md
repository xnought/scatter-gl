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
