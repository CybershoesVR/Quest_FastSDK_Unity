# Quest FastSDK Unity: Cybershoes
UnityFastSDK - one pager

///////////////////////////////// 
//  BASIC IMPLEMENTATION  /// 
/////////////////////////////////  
Any questions: please contact us dev@cybershoes.io  We are here to help.  
Replace what is written in "parenthesis" with your gameobject. This goes into your update.

```
float speed = 0.5f;
Vector3 gamepad3D = new Vector3(gamepad.leftStick.x.ReadValue(), 0.0, gamepad.leftStick.y.ReadValue());
"OVRPlayerController".transform.Translate(gamepad3D * Time.deltaTime * speed);

```
The Cybershoes receiver outputs a left stick x/y gamepad signal relative to the HMD orientation.  
This signal tells the game in which direction the shoes are pointing.  
Walking in the direction of the shoes works well, if the same factor is applied for speed y (forward) as for speed x (sidewards).  
Either you or we test how the speed feels. 

///////////////////////////////////// 
//  EXAMPLE PROJECT AND SEATED MODE  //////// 
/////////////////////////////////////  
Full example project including a suggestion for a seated mode:  
https://github.com/CybershoesVR/Quest_SDK_Unity2020-1_XRplugin_Example  
https://github.com/CybershoesVR/Quest_SDK_Unity2019-4_OculusPlugin_Example 

/////////////////////////////////
// BACKGROUND INFORMATION  //////
/////////////////////////////////

* Cybershoes users know that they should select HMD oriented movement in the game settings. 

* There are gyroscopes taking care of the correlation between shoes and headset. 
Cybershoes users know that in order to calibrate, they must point shoes forward, look forward, and press receiver button once. 

After above mentioned calibration you get:
* Y axis ("forward"): user looks forward & walks forward (shoes point forward)
* X axis ("strafing"): user looks e.g. to the left & walks forward (shoes point to the right side)
