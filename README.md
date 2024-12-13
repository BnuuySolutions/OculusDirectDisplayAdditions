# This project has been archived
This project is no longer supported anymore, and no support will be provided. However, this served as the basis for OVRSDK, which let me create ReLinked VR, my attempt at debloating the Oculus PCVR setup package by stripping it down to just the runtime, as well as OculusWRP, which completely strips the Oculus runtime and wraps OVR headset plugins around OpenVR driver APIs.

## OculusDirectDisplayAdditions
3rd-party "DirectDisplay" implementation which adds an "extended display" mode for the Oculus PC app, intended for Intel (and NVIDIA Optimus with HDMI wired to the Intel GPU) graphics.

This is only works for ***tethered*** Oculus headsets, such as the Rift S or CV1. It is useless for PCs (usually desktops and certain laptops) which have the HDMI/DisplayPort port wired to the NVIDIA GPU, or headsets which use Quest Link or Air Link.

## Notes
As this project largely consists of code that was reverse-engineered by myself over the span of a month (basically), there could be issues that can break OVRServer into a state which ***might*** require a system restart. I am not responsible for any hardware or system damage caused by this project, although it is very unlikely to cause any damage to either at all.

If you experience any crashes you think were caused by this project, please create an issue and describe to the best of your ability how to reproduce it (if possible) and if/any crash logs.

## How does this work?
As it turns out, OVRServer will actually check for 3rd-party DirectDisplay implementations on startup, as long as `HKEY_LOCAL_MACHINE\SOFTWARE\Oculus\DirectDisplayDLL` is a path to a DLL library which contains a few exports, etc. This is an undocumented feature in OVRServer.

This allows us to provide "DirectDisplay" support for GPUs other than AMD or NVIDIA, such as NVIDIA Optimus (HDMI wired to the Intel GPU, such as most laptops) or even Intel Arc (at some point). Thus, allowing you to use your tethered Oculus headsets on your PC with those unsupported GPUs.
