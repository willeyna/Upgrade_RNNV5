# Upgrade_RNN
Repository for IceCube-Upgrade RNN


**Background**   
This repository is for a Recurrent Neural Network (RNN) applied to simulated i3 data from the IceCube detector at the South Pole. The detector currently consists of 5,160 Digital Optical Modules (DOMs), each with one photomultiplier tube (PMT), situated on 86 strings between 1.5-2.5 km below the surface. The DOMs collect light emitted when a neutrino interacts with a nucleus in the ice, called an event. Depending on when, where, and how much light is detected, we can reconstruct properties of the neutrino like energy, zenith (vertical angle), and azimuth (horizontal angle), among other things. Each of these detections is called a hit.


**Problem**   
When neutrinos have a very high energy (usually <img src="https://render.githubusercontent.com/render/math?math=\geq"> 1 TeV), they emit a lot of light in the detector, making it much easier to reconstruct its energy, direction, event type, etc. However The central area of IceCube, known as DeepCore, has a higher instrument density that the rest of the detector. DeepCore is used to probe the low-energy regime of neutrino physics, typically on the scale of <img src="https://render.githubusercontent.com/render/math?math=10^1"> GeV. This is where the IceCube-Upgrade comes in. The Upgrade is deploying 7 new stings, each with approximately 100 DOMs, into the DeepCore area. The Upgrade will also make use of two new DOM designs: the D-Egg with two PMTs (one on top, one on bottom), and the mDOM with 24 PMTs scattered over its surface. In total, Gen-1 and the Upgrade will have 15,700 PMTs. With these new DOMs they hope to improve energy reconstruction of low-energy events to the scale of <img src="https://render.githubusercontent.com/render/math?math=10^0"> GeV, as well as improve directional reconstruction.


**Data**   
IceCube uses a specific data type referred to as 'i3.' This data type is specific to IceCube and can be accessed using a module called I3Tray/IceTray. This module stores information about the event, as well as detector status, detector geometry.


**RNN**   
The RNN is neural network designed to handle data with a sequential (e.g. temporal) relationship, which is great for IceCube. The RNN takes in three input variables per event: a list of times when light was detected, a list of charges (proprotional to how much light was detected), and a list of generated IDs that describe which PMTs were triggered. Each of the corresponding entries in these lists (e.g. <img src="https://render.githubusercontent.com/render/math?math=t_1">, <img src="https://render.githubusercontent.com/render/math?math=q_1">, <img src="https://render.githubusercontent.com/render/math?math=p_1">) would comprise one hit, and all three lists comprise one event. The RNN outputs energy, dx/dy/dz direction, and error estimates for all four.
