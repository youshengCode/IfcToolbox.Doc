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

