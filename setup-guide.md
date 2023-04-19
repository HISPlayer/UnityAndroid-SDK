# Setup Guide

Through this guide, you will be introduced to the basic steps for setting up the playback.

## Import package

Importing the package is the same as importing other normal packages in Unity. 
Select the package of HisPlayer SDK and import it.

**Assets > Import Package > Custom Package**

![](/assets/import-package.png)

<br>

## Configure Unity for Android

Open the window HISPlayer located in the upper side of the screen.

![](/assets/configure-unity.png)

Select Android target (this action will change the target platform for Unity).

![](/assets/android-target.png)

Press the buttons inside the window and settings will be updated.

## Setup HISPlayer Manager

Create a new script which will inherit from **HisPlayerManager**  It is necessary to add the **'using HisPlayerAPI;'** dependancy.
Then, add this component to a new game object (recommended to be empty).

Call the ‘SetUpPlayer()’ function in order to initialize the stream environment internally. This function can be called whenever it’s needed.
For example, using the Awake function:

```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using HisPlayerAPI;

public class HISPlayerAndroidSample : HisPlayerManager
{
    protected override void Awake()
    {
        base.Awake();
        SetUpPlayer();
    }
}
```
It is strictly necessary to use SetUpPlayer before using anything else. This function initializes everything else that will be needed during the usage of HISPlayer APIs
