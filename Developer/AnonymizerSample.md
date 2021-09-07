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

