# Quick recipes

## Optimize with FPR for IfcPoint and IfcPointList

```c#
public static void Optimize(string filePath)
{
    Log.Information($"IfcOptimizer - Start");
    IConfigOptimize config = ConfigFactory.CreateConfigOptimize();
    config.PrecisionOpen = true;
    config.Precision = 4;
    config.OptimizePoint = true;
    config.OptimizePointList = true;
    config.MergeOpen = true;
    config.MergeOnlyResources = true;
    config.MergeReversedEntities = true;
    OptimizerProcessor.Process(filePath, config, true);
}
```

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

## Split model by IfcBuildingStorey with entity label

```c#
public static void SplitByBuildingStorey(string filePath)
{
    Log.Information($"IfcSplitter - Start");
    IConfigSplit config = ConfigFactory.CreateConfigSplit();
    config.LogDetail = true;
    config.SplitStrategy = SplitStrategy.ByBuildingStorey;
    config.SelectedItems = new List<string> { "137", "131" };
    SplitterProcessor.Process(filePath, config, true);
}
```

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

## Simply anonymize personal info

```c#
public static void AnonymizeUPersonalInfo(string filePath)
 {
     Log.Information($"IfcAnonymizer - Start");
     IConfigAnonymize config = ConfigFactory.CreateConfigAnonymize();
     config.LogDetail = true;
     config.AnonymeUserInfo = true;
     config.RemoveAllUserInfo();
     AnonymizerProcessor.Process(filePath, config, true);
 }
```

## Anonymize product info with rules

```c#
 public static void AnonymizeProductInfoWithRules(string filePath)
 {
     Log.Information($"IfcAnonymizer - Start");
     IConfigAnonymize config = ConfigFactory.CreateConfigAnonymize();
     config.LogDetail = true;
     config.AnonymeProductInfo = true;
     config.ReplaceAllInProductInfo();
     List<AnonymeRule> rules = new List<AnonymeRule>();
     rules.Add(new AnonymeRule("IfcFurniture", "Furniture_Couch_Viper", "Unknown"));
     rules.Add(new AnonymeRule("IfcFurniture", "Furniture_Table_Dining_w", "Unknown"));
     config.Rules = rules;
     AnonymizerProcessor.Process(filePath, config, true);
 }
```



