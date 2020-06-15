# WVU Robotics Bramblebee Gazebo Model

This repository houses all packages for the Bramblebee Gazebo model. See
`simulator-pollination` for the main repository to run pollination simulations.

### TODO
- Should `bramblebee_gazebo/src/GazeboRosVelodyneLaser.cpp` be organized in
`plugins`?
- Will `rosdep` pull in the Husky packages?
- Is it possible to associate this model with Gazebo physics parameters? The
answer is probably "no" since multiple models may exist in a single world, but
some equivalent will be helpful. Bramblebee seems to rotate best when its
world's friction model is set to [cone_model](http://sdformat.org/spec?ver=1.7&elem=physics#solver_friction_model),
as seen in the <physics> block of `bramblebee_gazebo/worlds/clearpath_playpen.world`.
- Don't include the playpen world here. It's essentially a duplicate of the
Husky playpen world with some physics parameters changed.
