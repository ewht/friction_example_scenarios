# friction_example_scenarios
To mess around with the SUMO Friciton Feature

Only works with my fork (tested under Windows 10 and Ubuntu 20.04): https://github.com/ewht/sumo

What it is:

Basically just an extension of the network properties by a "friction" attribute, supposed to represent the available friction between a vehicle and the road. (See publications)
 -> Netloader and Netbuilder has been adapted to load "old" networks and set a default friction value of 1.0
 -> Neteditor full integration
 -> Full TraCI integration (get/set) via lane or edge. In case of edge, it is actually the mean friction value of all the lanes of that edge.
 -> There is an "additional" implementation "VariableFrictionCoefficient" working like the VariableSpeedSign, just for the friction value if you need it to be dynamic.
 -> otherwise change it via TraCI at runtime (thats what I usually did using matlab and python scripts for sets of simulations...)

However, it comes with two adapted CarFollowing Models, KraussFric (the default one with an adaptation) and ACCFric.
 -> KraussFric mimics a Human drivers behavior of going a little slower with deteriorating Weather (=Friction) conditions (see also the pubs)
 -> ACCFric enhances the "saftey" distance and adapts speed (if necessary) depending on the prevelant friction value. 
 --> Note that in both cases they behave exacetly like their parent for a value (default) of 1.0! --> That is a feature :)

Furthermore it comes with a device (MSDevice_Seeroad) which mimics a sensor system that you can equipp to a vehicle that "measures" the value on the road.
It comes with a statistical model, for simplicity it is only a white noise. You can adapt:
- the standard deviation "device.Seeroad.stdev"
- and add a fixed offset (systematic measurement error) "device.Seeroad.offset"
if you want via the custom attributes.

I pulled and merged with the version from Mar 16 11 a.m. (1.12.xxx) and compiled Windows and Ubuntu 20.04 LTS both working and passing my personal tests.
You can find example scenarios to play and test with here: (same github as the fork) 


References:

Dissertation: (English)
https://doi.org/10.17185/duepublico/75278
On the Potential of a Weather-Related Road Surface Condition Sensor Using an Adaptive Generic Framework in the Context of Future Vehicle Technology

Abschlussbericht: (Final Project Report (German))
https://doi.org/10.2314/KXP:1741603366
Sensorsystem zur autonomen Fahrbahnzustandserkennung (SEEROAD) : Abschlussbericht : Teilvorhabenbezeichnung: Fahrzeugmodell, Fahrzeugsimulation : Laufzeit: 1. März 2017-29.Februar 2020

SUMO User Conference 2019 (English)
https://doi.org/10.29007/cqps
Introducing Road Surface Conditions into a Microscopic Traffic Simulation
