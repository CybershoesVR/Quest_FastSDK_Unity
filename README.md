# Quest FastSDK Unity: Cybershoes


**IMPLEMENTATION**  
Replace what is written in "parenthesis" with your gameobject. This goes into your update.

```
float speed = 0.5f;
Vector3 gamepad3D = new Vector3(gamepad.leftStick.x.ReadValue(), 0.0, gamepad.leftStick.y.ReadValue());
"OVRPlayerController".transform.Translate(gamepad3D * Time.deltaTime * speed);

```
The Cybershoes receiver outputs a left stick x/y gamepad signal relative to the HMD orientation.  
This signal tells the game in which direction the shoes are moving.  
Walking in the direction of the shoes works well, if the same factor is applied for speed y (forward) as for speed x (sidewards).  
Either you or we test how the speed feels. 

**EXAMPLE PROJECT AND SEATED MODE**  
Full example project including a suggestion for a seated mode:  
https://github.com/CybershoesVR/Quest_SDK_Unity2020-1_XRplugin_Example  
https://github.com/CybershoesVR/Quest_SDK_Unity2019-4_OculusPlugin_Example 

**BACKGROUND INFORMATION**  

* On https://www.cybershoes.com/questsetup/ [Game HINTS] we explain what setting to choose in game.

* There are gyroscopes taking care of the correlation between shoes and headset. 
Cybershoes users know that in order to calibrate, they must point shoes forward, look forward, and press receiver button once. 

After above mentioned calibration you get:
* Y axis ("forward"): user looks forward & walks forward (shoes point forward)
* X axis ("strafing"): user looks e.g. to the left & walks forward (shoes point to the right side)

Any questions: please contact us dev@cybershoes.com  We are here to help. 
