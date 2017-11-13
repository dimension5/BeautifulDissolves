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

## Dissolve Settings
| Setting        | Description  |
| ------------- |:-------------:|
| Dissolve Map     | The dissolve pattern, uses the red (R) channel of the texture map (lower/darker values dissolve faster) |
| Direction Map      | The direction of dissolve controlled by the red (R) channel of the texture map (lower/darker values dissolve faster)     |
| Dissolve Mask | The dissolve mask, uses the alpha (A) channel of the texture map (0 = no dissolve, 1 = dissolve)      |
| Dissolve Amount | The amount of dissolve to apply (0 = no dissolve, 1 = fully dissolved) (range 0-1) |
| Dissolve Delay | The amount of delay before dissolving begins (range 0-1) |
| Dissolve Ramp Up | The speed at which dissolve glow/colors will reach its maximum peak (range 1-10) |
| Substitute Texture | The texture to use inplace of clipping (RGB) |
| Use Color Ramp | Switch between using a texture color ramp (RGB) for dissolve edges or interpolated colors (boolean) |
| Color Ramp (only if Use Color Ramp is set) | The color ramp (RGB) to use for the dissolve edge color |
| Inner/Outer Edge Color (only if Use Color Ramp is NOT set) | The color(s) (RGB) for the dissolve edge, color is interpolated between inner and outer edge colors |
| Edge Thickness | The thickness of the dissolve edge (range 0-1) |
| Dissolve Glow | Switch between using a dissolve emission glow or not (boolean) |
| Glow Color | Color (RGB) of the dissolve glow |
| Glow Intensity | The intensity of the dissolve glow (range 0-1) |
| Follow-Through | If a Substitute texture is used, this will determine whether the substitute will also glow or not (boolean) |
