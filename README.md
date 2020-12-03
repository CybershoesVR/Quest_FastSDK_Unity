# UnityFastSDK
UnityFastSDK - one pager

/////////////////////////////////
// BACKGROUND INFORMATION  //////
/////////////////////////////////


The Cybershoes receiver outputs a left stick x/y gamepad signal. 
This shoe movement vector is given relative to the HMD orientation 
Cybershoes users know that they should select HMD oriented movement in the game settings. 
There are IMUs (gyroscopes) in receiver and shoes taking care of the correlation between shoes and headset. 
Cybershoes users know that in order to calibrate, they point shoes forward, look forward, and press receiver button once. 

After above mentioned calibration: 
* user looks forward & shoes point forward >>> Y-value ("forward") 
* user looks to the left side & shoes point forward >>>X-value ("strafing") 

Full example project including a suggestion for a seated mode: https://github.com/CybershoesVR/Quest_SDK_Unity_Example 

///////////////////////////////// 
// BASIC IMPLEMENTATION  //////// 
///////////////////////////////// 
Any questions: please shoot us an email at dev@cybershoes.io 
E.g. You might be on another version of the Oculus SDK. 
We are here to help. 



```using Cybershoes;``` //include script file: "CybershoesInput.cs"  

 

```"OVRPlayerController".transform.Translate(GetCybershoesInput());``` //apply movement 
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
