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

