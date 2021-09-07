[toc]

# Flowchars

## Original

```
graph LR

    302("#302= IFCWALLSTANDARDCASE('0czCsOQ5z4dg8QGBRFInu2',$,$,$,$,#305,#320,$,$);")

    302 --> 305
    subgraph #305
    305("#305= IFCLOCALPLACEMENT($,#306);")
    306("#306= IFCAXIS2PLACEMENT3D(#307,#308,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 --> 307
    306 --> 308
    306 --> 309
    end

    302 --> 320
    subgraph #320
        320("#320= IFCPRODUCTDEFINITIONSHAPE($,$,(#313,#319));")

        320 --> 313
        subgraph #313
            313("#313= IFCSHAPEREPRESENTATION(#11,'Axis','Curve2D',(#312));")
            11("#11= IFCGEOMETRICREPRESENTATIONSUBCONTEXT('Axis','Model',*,*,*,*,#7,$,.MODEL_VIEW.,$);")
            313 --> 11
            313 --> 312
            subgraph #312
                312("#312= IFCPOLYLINE((#311,#310));")
                310{{"#310= IFCCARTESIANPOINT((5000.0,0.0));"}}
                311{{"#311= IFCCARTESIANPOINT((0.0,0.0));"}}
                312 --> 310
                312 --> 311
            end
        end

        320 --> 319
        subgraph #319
        319("#319= IFCSHAPEREPRESENTATION(#12,'Body','SweptSolid',(#318));")
        319 --> 12
        12("#12= IFCGEOMETRICREPRESENTATIONSUBCONTEXT('Body','Model',*,*,*,*,#7,$,.MODEL_VIEW.,$);")
            319 --> 318
            subgraph #318
            318("#318= IFCEXTRUDEDAREASOLID(#316,$,#317,2000.0);")
            317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
            316("#316= IFCRECTANGLEPROFILEDEF(.AREA.,'Wall Perim',#314,5000.0,270.0);")
            314("#314= IFCAXIS2PLACEMENT2D(#315,$);")
            315{{"#315= IFCCARTESIANPOINT((2500.0,135.0));"}}
            318 --> 317
            318 --> 316
            316 --> 314
            314 --> 315
            end
        end

        11 --> 7
        12 --> 7
        subgraph #7
        7("#7= IFCGEOMETRICREPRESENTATIONCONTEXT($,'Model',3,0.0001,#8,#10);")
        8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
        9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
        10[/"#10= IFCDIRECTION((0.0,1.0));"/]
        7 --> 8
        7 --> 10
        8 --> 9
        end
    end
```

## Focus

```
graph LR

    302("#302")

    302 --> 305
    subgraph #305
    305("#305")
    306("#306= IFCAXIS2PLACEMENT3D(#307,#308,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 --> 307:::samePoint
    306 --> 308:::sameDirection
    306 --> 309
    end

    302 --> 320
    subgraph #320
        320("#320")

        320 --> 313
        subgraph #313
            313("#313")
            11("#11")
            313 --> 11
            313 --> 312
            subgraph #312
                312("#312")
                310{{"#310= IFCCARTESIANPOINT((5000.0,0.0));"}}
                311{{"#311= IFCCARTESIANPOINT((0.0,0.0));"}}
                312 --> 310
                312 --> 311
            end
        end

        320 --> 319
        subgraph #319
        319("#319")
        319 --> 12
        12("#12")
            319 --> 318
            subgraph #318
            318("#318")
            317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
            316("#316")
            314("#314= IFCAXIS2PLACEMENT2D(#315,$);")
            315{{"#315= IFCCARTESIANPOINT((2500.0,135.0));"}}
            318 --> 317:::sameDirection
            318 --> 316
            316 --> 314
            314 --> 315
            end
        end

        11 --> 7
        12 --> 7
        subgraph #7
        7("#7")
        8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
        9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
        10[/"#10= IFCDIRECTION((0.0,1.0));"/]
        7 --> 8
        7 --> 10
        8 --> 9:::samePoint
        end
    end
    classDef samePoint fill:#09f;
    classDef sameDirection fill:#0f9;
```

## Merge

```
graph LR

    302("...")

    302 --> 305
    subgraph #305
    305("#305")
    306("#306= IFCAXIS2PLACEMENT3D(#307,#308,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 -.- 307:::garySec
    306 -.- 308:::garySec
    306 --> 309
    end

    302 --> 318
    subgraph #318
    318("#318")
    317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
    316("#316")
    318 --> 316
    318 --> 317:::sameDirection
    end

    302 --> 7
    subgraph #7
    7("#7")
    8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
    9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    10[/"#10= IFCDIRECTION((0.0,1.0));"/]
    7 --> 8
    7 --> 10
    8 --> 9:::samePoint
    end

    306 --> 9
    306 --> 317
    classDef samePoint fill:#09f;
    classDef sameDirection fill:#0f9;
    classDef garySec fill:#666;
```



## Merge recursive start

```
graph LR

    302("...")

    302 --> 305
    subgraph #305
    305("#305")
    306("#306= IFCAXIS2PLACEMENT3D(#9,#317,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 -.- 307:::garySec
    306 -.- 308:::garySec
    306 --> 309
    end

    302 --> 318
    subgraph #318
    318("#318")
    317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
    316("#316")
    318 --> 316
    318 --> 317:::sameDirection
    end

    302 --> 7
    subgraph #7
    7("#7")
    8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
    9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    10[/"#10= IFCDIRECTION((0.0,1.0));"/]
    7 --> 8:::redSec
    7 --> 10
    8 --> 9:::samePoint
    end

    306 --> 9
    306 --> 317
    classDef samePoint fill:#09f;
    classDef sameDirection fill:#0f9;
    classDef garySec fill:#666;
    classDef redSec fill:#fa0;
    
    
    50("#50= IFCBUILDING('0Cd2Mw3cP09wW6qWHK8v2f',$,'IfcBuilding',$,$,#51,$,$,.ELEMENT.,$,$,#57);")
    51("#51= IFCLOCALPLACEMENT($,#52);")
    52("#52= IFCAXIS2PLACEMENT3D(#53,$,$);")
    53{{"#53= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    57("#57= IFCPOSTALADDRESS($,$,$,$,$,$,$,'Unknown',$,$);")
    50 --> 51
    subgraph #51
    51 --> 52:::redSec --> 53:::samePoint
    end
    50 --> 57
```

## Merge recursive second

```
graph LR

    302("...")

    302 --> 305
    subgraph #305
    305("#305")
    306("#306= IFCAXIS2PLACEMENT3D(#9,#317,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 -.- 307:::garySec
    306 -.- 308:::garySec
    306 --> 309
    end

    302 --> 318
    subgraph #318
    318("#318")
    317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
    316("#316")
    318 --> 316
    318 --> 317:::sameDirection
    end

    302 --> 7
    subgraph #7
    7("#7")
    8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
    9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    10[/"#10= IFCDIRECTION((0.0,1.0));"/]
    7 --> 8:::redSec
    7 --> 10
    8 --> 9:::samePoint
    end

    306 --> 9
    306 --> 317
    classDef samePoint fill:#09f;
    classDef sameDirection fill:#0f9;
    classDef garySec fill:#666;
    classDef redSec fill:#fa0;
    
    
    50("#50")
    51("#51= IFCLOCALPLACEMENT($,#52);")
    52("#52= IFCAXIS2PLACEMENT3D(#9,$,$);")
    53{{"#53= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    57("#57")
    50 --> 51
    subgraph #51
    51 --> 52:::redSec -.- 53:::garySec
    end
    50 --> 57
    52 --> 9
```

## Final

```
graph LR

    302("...")

    302 --> 305
    subgraph #305
    305("#305")
    306("#306= IFCAXIS2PLACEMENT3D(#9,#317,#309);")
    307{{"#307= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    308[/"#308= IFCDIRECTION((0.0,0.0,1.0));"/]
    309[/"#309= IFCDIRECTION((1.0,0.0,0.0));"/]
    305 --> 306
    306 -.- 307:::garySec
    306 -.- 308:::garySec
    306 --> 309
    end

    302 --> 318
    subgraph #318
    318("#318")
    317[/"#317= IFCDIRECTION((0.0,0.0,1.0));"/]
    316("#316")
    318 --> 316
    318 --> 317:::sameDirection
    end

    302 --> 7
    subgraph #7
    7("#7")
    8("#8= IFCAXIS2PLACEMENT3D(#9,$,$);")
    9{{"#9= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    10[/"#10= IFCDIRECTION((0.0,1.0));"/]
    7 --> 8:::redSec
    7 --> 10
    8 --> 9:::samePoint
    end

    306 --> 9
    306 --> 317
    classDef samePoint fill:#09f;
    classDef sameDirection fill:#0f9;
    classDef garySec fill:#666;
    classDef redSec fill:#fa0;
    
    
    50("#50")
    51("#51= IFCLOCALPLACEMENT($,#8);")
    52("#52= IFCAXIS2PLACEMENT3D(#9,$,$);")
    53{{"#53= IFCCARTESIANPOINT((0.0,0.0,0.0));"}}
    57("#57")
    50 --> 51
    subgraph #51
    51 -.- 52:::garySec -.- 53:::garySec
    end
    50 --> 57
    51 --> 8
```



