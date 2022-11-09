# LIDAR Scanner

This app is intended to be a proof of concept for collecting lidar point
clouds on one of the newer iOS devices and uploading them to a repository of some kind.

The iOS LIDAR scanner is integrated with ARKit.  As such it's optimized
  for displaying things on a device screen and having AR items interact
  with real-world things (Pikachu being partially occluded because he's
  standing behind a person, or an AR ball
  colliding with an actual wall.)

The purpose of this app will be to answer a few questions and
determine how useful LIDAR scanning would be outside of Apple's intended
use case.

## Basic architecture for the App

- One screen with a camera view and a capture button.

- The camera view should display the ARKit's `sceneReconstruction` to
  verify the points you're collecting.  [See
  here](https://developer.apple.com/documentation/arkit/content_anchors/visualizing_and_interacting_with_a_reconstructed_scene)
  for details about that.

- When the button is pressed:
  - Collect the mesh data from ARKit as
    [ARMeshGeometry](https://developer.apple.com/documentation/arkit/armeshgeometry)


  - (Possibly) Correct the coordinates of the mesh.  I don't know if
    ARKit already does this math for you, or if it uses coordinates
    based on your screen, and thus you'd have to read
    about the device orientation from another service and manually
    correct.

  - Save to device file system

  - Upload to a service (Firebase?)


## Open Questions

- What kind of limitations does the LIDAR device have? Range, precision,
  etc.

- What is the coordinate system we get from the mesh, and do we need to
  correct?


## For the Future

- Ray tracing, collision detecting

## Resources:

- Apple demo code for collecting a mesh:
<https://developer.apple.com/documentation/arkit/content_anchors/visualizing_and_interacting_with_a_reconstructed_scene>

- Apple demo code for collecting a depth map:
<https://developer.apple.com/documentation/arkit/environmental_analysis/displaying_a_point_cloud_using_scene_depth>

- Some info about exporting LIDAR data to a .obj file:
<https://stackoverflow.com/questions/61063571/arkit-how-to-export-obj-from-iphone-ipad-with-lidar>

- Some other pages:
  - <https://www.it-jim.com/blog/iphones-12-pro-lidar-how-to-get-and-interpret-data/>

  - <https://www.nomtek.com/blog/lidar-scanner-research>

- Scaniverse: an app using LIDAR.  (There are plenty of others, but this
  one seems to be the most feature-rich)
  <https://scaniverse.com/>
