**Dev Log #06 — Post-load contact hotfix**

The HMD retest showed that touch/kiss could still stop working after loading a scene in 0.8.0.

I reproduced another cause: when the native Settings panel had never been opened, its touch-setting handler was not initialized. Loading a disabled touch setting then changed the wrong collision layers, disabling unrelated contacts too.

The loader now initializes that handler before applying the saved value. A new test uses actual Unity collision callbacks and covers switching touch off/on while the native panel stays closed. It fails on the previous code and passes with the fix.

Please fully restart the game after installing 0.8.1. Existing saves do not need to be recreated. Character Touch retains its original hand/body enable-disable behavior.

Physical HMD confirmation is still pending. This fixes a reproduced collision-policy defect; it is not a claim that every controller-related issue has been verified.

https://github.com/CrouchingWriter/MeltySave
