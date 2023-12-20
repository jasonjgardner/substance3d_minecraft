# _labPBR Preview_ Filter Usage

## Substance Designer

### Specular Texture Parameters

#### f0

Manage the level of reflectivity. Shows in the green channel.

##### Metal Source

Select `f0` to convert the material input's metallic channel to the f0 value.
Select `Use preset` to select from a list of presets provided by
**[Luke-Marchant/labpbr-substance-tools](https://github.com/Luke-Marchant/labpbr-substance-tools/ "View the GitHub repository ❤️")**.

##### Metal Preset

If `Use preset` is selected, a dropdown list of hardcoded metal values and
common dielectrics is shown.

#### Surface

Manage the subsurface scattering and porosity values. Shows in the blue channel.

##### Assignment

Select `Subsurface scattering` to use only the SSS value in the specular
texture's blue channel, `Porosity` to use only a porosity value, or
`Blend SSS with porosity`. Selecting to blend the two values will reveal inputs
for blending mode and opacity.

#### Emissive

Clamps the emissive level. Shown in the alpha channel. Set to `0` to remove the
alpha channel.

### Normal Map Texture Parameters

#### POM

Select the source of parallax object mapping in the dropdown menu. Select
`Custom input` to provide a displacement map. Select `Use heightmap` to use the
material height as the POM depth. Selecting `Disable POM` will exclude the depth
map from the alpha channel.

#### Ambient Occlusion

Select `Use input` to provide a material's AO output. (Provide a entirely white
texture input to disable AO output.) Otherwise, `Convert height to AO` will
generate AO from the material's height. Selecting this option will reveal
settings to manage AO spreading and levels.

## Substance Painter

### Previewing labPBR Textures

Activate the `User1` and `User2` channels under the **Channels** section in the
**Texture Set Settings** window. Click the cog icon to set the colorspace to
`sRGB8`. The `Color channel` option should also be selected.

Add filter in the **Layers** window. This will enable the specular texture
output in the shader's `User1` channel and the normal map the in the `User2`
channel. Select these channels from the dropdown list in the 2D/3D viewport to
enable the labPBR output preview.

([See _Substance Designer_ section](#substance-designer) for a description of
parameter usage.)

### Exporting labPBR Textures

Create a new Output Template preset which includes **RGB+A** output maps named
`$textureSet_s` and `$textureSet_n`.

Drag the `User1` channel from the **Input maps** section into the RGB channel of
the `$textureSet_s` output. Drag the user channel once again to the output map,
and drop it in the alpha channel (labeled _A_). Select the **A Channel** option
after dropping `User1` into _A_.

Repeat the process with the `User2` channel into `$textureSet_n`'s RGB+A
channels.
