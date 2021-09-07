# IFC Optimizer

Overview

IFC Optimizer is a tool for reduce the size of an IFC file. Along with the BIM project becomes more complicated and more detailed, sometimes IFC files can become rather large. And that lead to an expensive computational costs for processing IFC files. 



Generally, this important size is due to duplicate entity instances. 

Here is a simple from buildingSMART International with just one IfcWallStandardCase in it. We take a small piece of it. 

```
#7= IFCGEOMETRICREPRESENTATIONCONTEXT($,'Model',3,0.0001,#8,#10);
#8= IFCAXIS2PLACEMENT3D(#9,$,$);
#9= IFCCARTESIANPOINT((0.0,0.0,0.0));
#10= IFCDIRECTION((0.0,1.0));

#50= IFCBUILDING('0Cd2Mw3cP09wW6qWHK8v2f',$,'IfcBuilding',$,$,#51,$,$,.ELEMENT.,$,$,#57);
#51= IFCLOCALPLACEMENT($,#52);
#52= IFCAXIS2PLACEMENT3D(#53,$,$);
#53= IFCCARTESIANPOINT((0.0,0.0,0.0));
```



The goal of this tutorial is to reduce the size of an IFC file. Indeed, IFC files can become rather large and processing them can lead to expensive computational costs. Most of the time, this important size is due to duplicate entity instances. In this tutorial, we're going to see how to create a newly optimized file which doesn't contain those instances.

[IfcOpenShell Optimizer tutorial | IfcOpenShell Academy](https://academy.ifcopenshell.org/posts/ifcopenshell-optimizer-tutorial/)

[IFCCompressor: A content-based compression algorithm for optimizing Industry Foundation Classes files (tsinghua.edu.cn)](http://cgcad.thss.tsinghua.edu.cn/liuyushen/main/pdf/LiuYS_AIC15IFCCompressor.pdf)

[Solibri | Solibri IFC Optimizer](https://www.solibri.com/solibri-ifc-optimizer)

[Added nested list support when get referring types. by youshengCode · Pull Request #385 · xBimTeam/XbimEssentials (github.com)](https://github.com/xBimTeam/XbimEssentials/pull/385)

```
Working in progress...
```

## How FPR improve IFC file quality ?

```
Working in progress...
```

## How merge redundancy process can be zero loss ?

```
Working in progress...
```

