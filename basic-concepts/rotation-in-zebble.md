[xyz]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/rotation-in-zebble/xyz.png "Zebble-Rotation"
[z]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/rotation-in-zebble/z.png "Zebble-Rotation"
[x]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/rotation-in-zebble/x.png "Zebble-Rotation"
[y]: https://raw.githubusercontent.com/Geeksltd/Zebble.Docs/master/assets/basic-concept/rotation-in-zebble/y.png "Zebble-Rotation"

### ROTATION IN ZEBBLE

Zebble framework includes first-class support for rotating views in three dimensions. Every View instance exposes Rotation, RotationX, and RotationY as values that can be set or bound.

Rotation is interpreted as a degree value rather than a radian or gradian value.

Rotation values apply to the axes as follows:

- **Rotation** – rotates around the Z-axis. When holding a phone normally, the Z-axis extends out towards the user.
- **RotationX** – rotates around the X-axis. When holding a phone normally, the X-axis extends out towards the user's left and right.
- **RotationY** – rotates around the Y-axis. When holding a phone normally, the Y-axis extends down towards the ground and up towards the sky.

See the following illustration to better understand how objects are rotated around the axes:

![xyz]
 

#### Rotation

The Rotation property rotates the view around the z-axis. The next image is rotated 52 degrees about the z-axis:

![z]
 

#### RotationX

The RotationX property rotates the view around the x-axis. The next image is rotated 73 degrees about the x-axis:


![x]


#### RotationY

The RotationY property rotates the view around the y-axis. The next image is rotated 122 degrees about the y-axis:


![y]