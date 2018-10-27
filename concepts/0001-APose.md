- Start Date: 2018-10-26
- RFC PR:
- MRPT Issue:

# Summary

APose concept is a pose in an arbitrary number of spatial dimensions, but typically 2D or 3D.

# Basic example

This concept generalizes the various types such as MRPT's CPose2D and CPose3D and ROS's geometry_msgs/Pose.

# Motivation

To generalize the poses for use with various algorithms

# Detailed design

One possible implementation of the APose concept: 
```
template<typename T>
concept bool APose = requires(T a){
        { a.dims } -> std::size_t;
        { a.position } -> APoint&;
        { a.orientation } -> AOrientation&;
};
```
APoint and AOrientation concepts are to be defined.

# Drawbacks
TBD

# Alternatives

position and orientation are also sometimes called translation and rotation. Also APoint may be refered to as a translation vector
```
template<typename T>
concept bool APose = requires(T a){
        { a.dims } -> std::size_t;
        { a.translation } -> AVector&;
        { a.rotation } -> ARotation&;
};
```

# Adoption strategy
TBD
# How we teach this
TBD
# Unresolved questions
TBD
