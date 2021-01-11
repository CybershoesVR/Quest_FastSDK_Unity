# UnityFastSDK
UnityFastSDK - one pager

///////////////////////////////// 
//  BASIC IMPLEMENTATION  //////// 
/////////////////////////////////  

Replace what is written in "parenthesis" with your gameobject.  
Any questions: please contact us dev@cybershoes.io  We are here to help. 

```
float speed = 0.5f;
Vector3 gamepad3D = new Vector3(gamepad.leftStick.x.ReadValue(), 0.0, gamepad.leftStick.y.ReadValue());
"OVRPlayerController".transform.Translate(gamepad3D * Time.deltaTime * speed);

```
Either you or we test how the speed feels. In some cases the sign (+/-) needs to be inverted.

///////////////////////////////////// 
//  EXAMPLE PROJECT AND SEATED MODE  //////// 
/////////////////////////////////////  
Full example project including a suggestion for a seated mode: https://github.com/CybershoesVR/Quest_SDK_Unity_Example '

/////////////////////////////////
// BACKGROUND INFORMATION  //////
/////////////////////////////////

The Cybershoes receiver outputs a left stick x/y gamepad signal.  

* The shoe movement vector is given relative to the HMD orientation 
Cybershoes users know that they should select HMD oriented movement in the game settings. 

* There are IMUs (gyroscopes) in receiver and shoes taking care of the correlation between shoes and headset. 
Cybershoes users know that in order to calibrate, they must point shoes forward, look forward, and press receiver button once. 

After above mentioned calibration you get:
* Y axis ("forward"): user looks forward & walks forward (shoes point forward)
* X axis ("strafing"): user looks e.g. to the left & walks forward (shoes point to the right side)
