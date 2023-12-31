# Introduction

For technical projects where for example communication between different systems, or automated functions have to be defined, pictures say more than a thousand words. What you design will be used by your colleagues, reviewed by your teachers, or used by your future self. So properly communicating your ideas is important.

To give you an idea on what you can do in approximately 30 lines of text:

```plantuml
@startuml pickup_parcel_from_coveyor
skinparam backgroundColor transparent
left to right direction
'skinparam linetype ortho

component box_pickup_application {
    
    [frame]
    () placement -u- frame
    [robot]
    () input_0 -- robot
    () output_0 -- robot
    () "end\neffector" -- robot

    [sensor]
    sensor --> input_0 : connected
    sensor --> "sensor\nposition"
    
    robot -> placement

    [cabinet]
    () "robot\npower" -- cabinet
    () "conveyor\npower" -- cabinet
   
    cabinet -u-> placement
    robot --> "robot\npower"
    cabinet -r-> output_0
    
    [conveyor]
    () "sensor\nposition" -- conveyor
    () "box\nposition" -- conveyor
    conveyor -> placement
    conveyor --> "conveyor\npower"

    [box]
    () shape -- box
    
    [gripper]
    gripper -l-> shape
    
    box --> "box\nposition"
    gripper --> "end\neffector"
}

[building]

() energy -l- building
() location -d- building

frame --> location
cabinet -r-> energy

@enduml
```
