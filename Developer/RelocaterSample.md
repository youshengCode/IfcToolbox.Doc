## Relocate model with specific IfcSite EntityLable

```c#
public static void RelocateToOrigin(string inputFileName, int ifcSiteEntityLable = 0)
{
    Log.Information($"IfcRelocate - Start");
    IConfigRelocate config = ConfigFactory.CreateConfigRelocate();
    config.LogDetail = true;
    config.AlignWorldCoordinates = true;
    config.AlignProjectCoordinates = true;
    config.WorldPlacement = GeoFactory.CreateGeoPlacement(new List<double> { 0, 0, 0 }, null, null);
    config.ProjectPlacements.Add(GeoFactory.CreateGeoPlacement(new List<double> { 0, 0, 0 }, null, null, ifcSiteEntityLable));
    RelocatorProcessor.Process(inputFileName, config, true);
}
```

