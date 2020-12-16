# UnityFastSDK
UnityFastSDK - one pager

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

Full example project including a suggestion for a seated mode: https://github.com/CybershoesVR/Quest_SDK_Unity_Example 

///////////////////////////////// 
//  IMPLEMENTATION  //////// 
/////////////////////////////////  

You might be on another version of the Oculus SDK. 
Any questions: please contact us dev@cybershoes.io 
We are here to help. 

```using Cybershoes;``` //include script file: "CybershoesInput.cs"  

```"OVRPlayerController".transform.Translate(GetCybershoesInput());``` //apply movement relative to HMD,call each frame
```
private Vector3 GetCybershoesInput()
{
    var gamepad = Gamepad.current;
    if (gamepad == null)
    {
        return new Vector3(0,0,0);
    }
    //get gamepad input
    Vector2 shoeMovement = new Vector2(gamepad.leftStick.x.ReadValue(), gamepad.leftStick.y.ReadValue());
    //use the Cybershoes script to get the optimal shoe orientation
    Vector2 adjustedShoeMovement = CybershoesInput.GetRotatedShoeVector("OVRCameraRig".centerEyeAnchor.rotation, shoeMovement);
    //test speed with Cybershoes to see if running feels fast enough
    float speed = 0.5f;
    //transform to vector3
    Vector3 characterMovement = new Vector3(-adjustedShoeMovement.x * Time.deltaTime * speed, 0, -adjustedShoeMovement.y * Time.deltaTime * speed);
    return characterMovement;
}  
```
