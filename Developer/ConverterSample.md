## Convert IFC to OBJ

```c#
public static void ConvertToObj(string filePath)
{
    Log.Information($"IfcConverter - Start");
    var convertOptions = new ConvertOptionsWrap();
    convertOptions.YUp = true;
    convertOptions.UseElementNames = true;
    IConfigConvert config = ConfigFactory.CreateConfigConvert(convertOptions, ConvertTargetFormat.OBJ);
    ConverterProcessor.Process(filePath, config, true);
}
```

## Extract 2D view as SVG from a file IFC

```c#
public static void ConvertToSvg(string filePath)
{
    Log.Information($"IfcConverter - Start");
    var convertOptions = new ConvertOptionsWrap();
    convertOptions.UseElementNames = true;
    convertOptions.Bounds = "1024x1024";
    convertOptions.PrintSpaceAreas = true;
    convertOptions.PrintSpaceNames = true;
    convertOptions.DoorArcs = true;
    convertOptions.ExcludeEntities = "IfcOpeningElement";
    IConfigConvert config = ConfigFactory.CreateConfigConvert(convertOptions, ConvertTargetFormat.SVG);
    ConverterProcessor.Process(filePath, config, true);
}
```

