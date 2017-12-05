# Beautiful Dissolves

The official repository for the [Unity "Beautiful Dissolves" asset found here.](https://www.assetstore.unity3d.com/en/#!/content/47771)

Beautiful Dissolves is a high-quality, powerful, and versatile shader that can help you enhance the look of your game!

## Getting Started

These instructions will get you started on using Beautiful Dissolves in your own projects.

## Prerequisites

1. Unity 5.1.0 or higher
2. GPU that supports shader model 3.0 or higher

## Features

* PBR Support
* 2D Support
* Mobile Support
* Over 60 Dissolve Maps Included
* ...and more!

## Dissolve Material Settings
| Setting        | Description  |
| ------------- |-------------|
| Dissolve Map **(R)**    | The dissolve pattern, uses the red (R) channel of the texture map (lower/darker values dissolve faster) |
| Direction Map **(R)**     | The direction of dissolve controlled by the red (R) channel of the texture map (lower/darker values dissolve faster)     |
| (\*)Dissolve Mask **(A)** | The dissolve mask, uses the alpha (A) channel of the texture map (0 = no dissolve, 1 = dissolve)      |
| Dissolve Amount **(0-1)** | The amount of dissolve to apply (0 = no dissolve, 1 = fully dissolved) |
| (\*)Dissolve Delay **(0-1)** | The amount of delay before dissolving begins |
| (\*)Dissolve Ramp Up **(1-10)** | The speed at which dissolve glow/colors will reach its maximum peak |
| Substitute Texture **(RGB)** | The texture to use inplace of clipping (RGB) |
| Use Color Ramp **(boolean)** | Switch between using a texture color ramp (RGB) for dissolve edges or interpolated colors |
| Color Ramp (only if Use Color Ramp is set) **(RGB)** | The color ramp (RGB) to use for the dissolve edge color |
| Inner/Outer Edge Color (only if Use Color Ramp is NOT set) **(RGB)** | The color(s) (RGB) for the dissolve edge, color is interpolated between inner and outer edge colors |
| Edge Thickness **(0-1)** | The thickness of the dissolve edge |
| Dissolve Glow **(boolean)** | Switch between using a dissolve emission glow or not |
| Glow Color **(RGB)** | Color (RGB) of the dissolve glow |
| Glow Intensity **(0-1)** | The intensity of the dissolve glow |
| Follow-Through **(boolean)** | If a Substitute texture is used, this will determine whether the substitute will also glow or not |

***(\*) These features are only available in Unity 2017.1.0 and higher.***

## Dissolve Helper Scripts

### Dissolve Settings Object (only available in v2.0.0 (Unity 2017.1.0 or higher))
A scriptable object that allows you to reuse dissolve settings for multiple gameobjects. Create a new ```DissolveSetting``` by using the menu option ```Create > BeautifulDissolves > Settings```.

#### Settings
| Setting        |  Description  |
| ------------- | -------------|
| Atomic | Controls whether the dissolve can be interrupted or not |
| Disable After Dissolve | Controls whether this object can be dissolved more than once |
| Dissolve Curve | An animation curve for the dissolve amount |
| Dissolve Start Percent | Percentage at which object should start dissolving from |
| Time | Amount of time the dissolve animation will take assuming speed is 1 |
| Speed | Allows you to "fast-forward" the animation. Similar to the ```Time``` parameter |

### Dissolve.cs
Add this script to any object with a Dissolve material to easily trigger dissolve by script.
```csharp
// Triggers dissolve using the DissolveSettings in the inspector
public void TriggerDissolve()

// Triggers dissolve using custom DissolveSettings object
public void TriggerDissolve(DissolveSettings settings)

// Triggers dissolve with custom parameters
public void TriggerDissolve(bool atomic, bool disableAfterDissolve, AnimationCurve dissolveCurve, float dissolveStartPercent, float time, float speed)

// Triggers a reverse dissolve using the DissolveSettings in the inspector
public void TriggerReverseDissolve()
```
#### Settings
| Setting        |  Description  |
| ------------- | -------------|
| Dissolve Settings | The dissolve settings to use for this dissolve (see above) |
| On Dissolve Start | The events that should trigger on dissolve start |
| On Dissolve End | The events that should trigger on dissolve end |

### DissolveGlowUpdate.cs
Add this script to any object with a Dissolve material to add a light source that will respond to the DissolveGlow property of the material. If ```Glow Source``` is set to ```Light``` then the script's inspector will allow you to create a Light source with a single-click that will update itself based on the current DissolveGlow properties (color, intensity).

![Dissolve glow script in action](https://github.com/dimension5/BeautifulDissolves/blob/master/images/DissolveGlow.gif)

#### Settings
| Setting        | Options | Description  |
| ------------- |------------- |-------------|
| Start Mode   | (\*)On Awake, On Start, By Script | When the glow will start updating |
| Update Rage | (\*)Every Frame, Every Nth Frame, Custom Fixed Timestep | The rate at which the glow will update |
| Glow Source | (\*)Emissive, Light | The source of glow, ```Emissive``` source requres the object to be set to ```Static```. If ```Light``` is selected then an option to auto-create a ```Light``` source is made available |
| Glow Cutoff | float (0-1) | The dissolve amount at which glow should be 0, this allows you to adjust for when the object is fully dissolved before it reaches a dissolve amount of 1 |

***(\*) Indicates default options***

### DissolveHelper.cs
This script allows you to easily change the dissolve shader properties during runtime. All dissolve properties are exposed through getters/setters, eg. ```SetDissolveMap(Material mat, Texture2D texture)``` allows you to change the dissolve map during runtime.

#### Example
```csharp
// In your own script
public void ChangeDissolveMap()
{
  DissolveHelper.SetDissolveMap(myDissolveMaterial, myDissolveMap);
}
```
