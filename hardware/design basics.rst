Design Basics
==========

Overview
__________
In Fusion 360 Design, there are 4 types of design. (Here listed in terms of usability)
    1. Solid / Sheet Metal (covers abbout 99.999999% of design we need to do)
    2. Form (creates a body using geometries instead of computations)
    3. Mesh (useful for editing STL or other non-computable geometries)
    4. Surface (use faces or something idk dont use this)

In robotics, we basically only use solids, and sheet metal sometimes (but we dont have fabrication capability so typical nah). In design, we want to use as many COTS (Commercial Off-The-Shelf) parts as possible. Our vendor is Gobilda. For custom parts, we have capability to print plastic parts (Contact Han for more information). 
However, these plastic parts are limited by their properties, such as the fact that plastic is less strong than metal. We would like to minimize using these parts and utilize 3D printed parts as mere modifications to already available parts. 

NOTE: If you do own a 3D-printer but don't know how to use it, contact Antonio. 

| Back to designing! 

Below is the typical workflow for creating a design. 
    1. Importing COTS (if applicable)
    2. Creating a sketch
    3. Creating a body
    4. Modifying a body
    5. Joints and assemblies

Importing COTS
_________________

Our COTS are from `Gobilda <https://www.gobilda.com>`_. 