# 3d printer fact sheet extraction


## Task 1
<details>
<summary>
Convert the following 3DGence 3d printer specification into a JSON_LD formatted Knowledge Graph. 
The node for this KG should be Printer as a main node, Type of 3d printer such as FDM, SLA, and SLS, Manufacturer, Material, Applications, and Technique.

</summary>
```
Convert the following 3DGence 3d printer specification into a JSON_LD formatted Knowledge Graph. 
The node for this KG should be Printer as a main node, Type of 3d printer such as FDM, SLA, and SLS, Manufacturer, Material, Applications, and Technique.

```Printer name:   Industry F340
Company: 3DGence

Specification 

PRINTING ENVIRONMENT
Print technology:  FFF Working temperature:  15-32°C
Build volume: 260 × 300 × 340 mm (26 520 cm3) Storage temperature:  0-32°C
Min. layer height: 40 μm
Number of printheads: 2 per module
Nozzle diameter: 0.4/0.4 mm or 0.6/0.6 mm
Filament diameter: 1.75 mm
POWER
Printhead temperature: 500°C
Buildplate temperature: 160°C Power requirements:  230V AC
Chamber temperature:  85°C (active heating) Max power draw:  2700 W
Filament chamber temperature:  70°C Communication:  USB drive, SD card
DIMENSIONS AND MASS SOFTWARE
External dimensions:  1200 × 800 × 1100 mm Slicing software:  3DGence SLICER 4.0
Mass:  200 kg
SAFETY
CONSTRUCTION
Filtration:  filtration unit
Chassis:   powder coated steel  UPS device:  yes, optional
Build surface: heated ceramic plate Others:  software access overdrive - remote 
Positioning resolution XY:  0.006 mm shut down
Positioning resolution Z:  0.0004 mm

NEW PAGE

Versatility
and best printing
IINNDDUUSSTTRRYY
results
FF334400
with job-specific printing 
modules and developed 
printing profiles
MMOODDUULLEESS
TEMPERATURE:
PRO
up to 265°C
NOZZLE DIAMETER:
0,4 mm/0,4 mm
MODEL MATERIAL:
ABS, PLA, PA, ASA, PP, TPU
SUPPORT MATERIAL:
ESM-10, HIPS, BVOH
TEMPERATURE:
HF
up to 265°C
NOZZLE DIAMETER:
0,6 mm/0,6 mm
MODEL MATERIAL:
ABS, ASA, PA-CF, PA-GF, PA, PP
SUPPORT MATERIAL:
ESM-10, HIPS
TEMPERATURE:
HT
up to 340°C
NOZZLE DIAMETER:
0,4 mm/0,4 mm
MODEL MATERIAL:
PC, PC-ABS, PC-ESD, PC-CF
SUPPORT MATERIAL:
ABS, ESM-10
TEMPERATURE:
HT
up to 500°C
NOZZLE DIAMETER:
max 0,4 mm/0,4 mm
MODEL MATERIAL:
PEEK, PEKK
SUPPORT MATERIAL:
ESM-10 
rev.1/2020 www.3dgence.com

NEW PAGE
```

</details>



### ChatGPT 3.5 Mar 23 Version Round 1


<details>
<summary>Answer 1:  &cross; interrupted data</summary>



```
{
  "@context": "https://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": "3DGence",
  "printTechnology": "FFF",
  "workingTemperature": {
    "@type": "Temperature",
    "value": "15-32°C"
  },
  "buildVolume": {
    "@type": "Dimensions",
    "length": "260mm",
    "width": "300mm",
    "height": "340mm",
    "volume": "26,520cm³"
  },
  "storageTemperature": {
    "@type": "Temperature",
    "value": "0-32°C"
  },
  "minLayerHeight": {
    "@type": "Distance",
    "value": "40μm"
  },
  "numberOfPrintheads": "2 per module",
  "nozzleDiameter": [
    "0.4/0.4 mm",
    "0.6/0.6 mm"
  ],
  "filamentDiameter": "1.75 mm",
  "printheadTemperature": {
    "@type": "Temperature",
    "value": "500°C"
  },
  "buildplateTemperature": {
    "@type": "Temperature",
    "value": "160°C"
  },
  "powerRequirements": {
    "@type": "Electricity",
    "voltage": "230V AC",
    "maxPowerDraw": "2700 W"
  },
  "chamberTemperature": {
    "@type": "Temperature",
    "value": "85°C"
  },
  "filamentChamberTemperature": {
    "@type": "Temperature",
    "value": "70°C"
  },
  "communication": [
    "USB drive",
    "SD card"
  ],
  "externalDimensions": {
    "@type": "Dimensions",
    "length": "1200mm",
    "width": "800mm",
    "height": "1100mm"
  },
  "slicingSoftware": "3DGence SLICER 4.0",
  "mass": {
    "@type": "Mass",
    "value": "200 kg"
  },
  "filtration": "filtration unit",
  "chassis": "powder coated steel",
  "upsDevice": "yes, optional",
  "buildSurface": "heated ceramic plate",
  "positioningResolutionXY": {
    "@type": "Distance",
    "value": "0.006mm"
  },
  "positioningResolutionZ": {
    "@type": "Distance",
    "value": "0.0004mm"
  },
  "material": [
    {
      "@type": "Material",
      "name": "ABS",
      "temperature": [
        {
          "@type": "Temperature",
          "value": "HF up to 265°C"
        },
        {
          "@type": "Temperature",
          "value": "HT up to 340°C"
        }
      ],
      "nozzleDiameter": [
        "0.4 mm/0.4 mm",
        "max 0.4 mm/0.4 mm"
      ],
      "supportMaterial": [
        "ESM-10",
        "HIPS",
        "BVOH",
        "ABS"
      ]
    },
    {
      "@type": "Material",
      "name": "PLA",
      "temperature": {
        "@type": "Temperature",
        "value": "PRO up to 265°C"

```


</details>


<details>
<summary>Answer 2:  &cross; interrupted data</summary>



```
{
  "@context": "https://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": "3DGence",
  "printTechnology": "FFF",
  "workingTemperature": "15-32°C",
  "buildVolume": "260 × 300 × 340 mm (26 520 cm3)",
  "storageTemperature": "0-32°C",
  "minLayerHeight": "40 μm",
  "numberOfPrintheads": "2 per module",
  "nozzleDiameter": ["0.4/0.4 mm", "0.6/0.6 mm"],
  "filamentDiameter": "1.75 mm",
  "printheadTemperature": "500°C",
  "buildplateTemperature": "160°C",
  "powerRequirements": "230V AC",
  "chamberTemperature": "85°C (active heating)",
  "maxPowerDraw": "2700 W",
  "filamentChamberTemperature": "70°C",
  "communication": ["USB drive", "SD card"],
  "externalDimensions": "1200 × 800 × 1100 mm",
  "slicingSoftware": "3DGence SLICER 4.0",
  "mass": "200 kg",
  "filtration": "filtration unit",
  "chassis": "powder coated steel",
  "upsDevice": "yes, optional",
  "buildSurface": "heated ceramic plate",
  "positioningResolutionXY": "0.006 mm",
  "positioningResolutionZ": "0.0004 mm",
  "temperatureModules": [
    {
      "@type": "TemperatureModule",
      "name": "PRO",
      "maxTemperature": "265°C",
      "nozzleDiameter": "0,4 mm/0,4 mm",
      "modelMaterials": ["ABS", "PLA", "PA", "ASA", "PP", "TPU"],
      "supportMaterials": ["ESM-10", "HIPS", "BVOH"]
    },
    {
      "@type": "TemperatureModule",
      "name": "HF",
      "maxTemperature": "265°C",
      "nozzleDiameter": "0,6 mm/0,6 mm",
      "modelMaterials": ["ABS", "ASA", "PA-CF", "PA-GF", "PA", "PP"],
      "supportMaterials": ["ESM-10", "HIPS"]
    },
    {
      "@type": "TemperatureModule",
      "name": "HT",
      "maxTemperature": "340°C",
      "nozzleDiameter": "0,4 mm/0,4 mm",
      "modelMaterials": ["PC", "PC-ABS", "PC-ESD", "PC-CF"],
      "supportMaterials": ["ABS", "ESM-10"]
    },
    {
      "@type": "TemperatureModule",
      "name": "HT",
      "maxTemperature": "500°C",
      "nozzleDiameter": "max 0,4 mm/0,4 mm",
      "modelMaterials": ["PEEK", "PEKK"],
      "supportMaterials": ["ESM-10"]
    }
  ],
  "applications": ["job-specific printing"],
  "technique": "developed printing profiles"
}

```


</details>


<details>
<summary>Answer 3: &cross; interrupted data</summary>



```
{
  "@context": {
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "schema": "http://schema.org/",
    "kg": "https://example.com/kg#",
    "name": "schema:name",
    "manufacturer": "schema:manufacturer",
    "type": "kg:type",
    "material": "kg:material",
    "application": "kg:application",
    "technique": "kg:technique",
    "temperature": "kg:temperature",
    "nozzle_diameter": "kg:nozzle_diameter",
    "model_material": "kg:model_material",
    "support_material": "kg:support_material",
    "print_technology": "kg:print_technology",
    "working_temperature": "kg:working_temperature",
    "build_volume": "kg:build_volume",
    "storage_temperature": "kg:storage_temperature",
    "min_layer_height": "kg:min_layer_height",
    "number_of_printheads": "kg:number_of_printheads",
    "filament_diameter": "kg:filament_diameter",
    "printhead_temperature": "kg:printhead_temperature",
    "buildplate_temperature": "kg:buildplate_temperature",
    "power_requirements": "kg:power_requirements",
    "chamber_temperature": "kg:chamber_temperature",
    "max_power_draw": "kg:max_power_draw",
    "filament_chamber_temperature": "kg:filament_chamber_temperature",
    "communication": "kg:communication",
    "external_dimensions": "kg:external_dimensions",
    "slicing_software": "kg:slicing_software",
    "mass": "kg:mass",
    "filtration": "kg:filtration",
    "chassis": "kg:chassis",
    "ups_device": "kg:ups_device",
    "build_surface": "kg:build_surface",
    "positioning_resolution_xy": "kg:positioning_resolution_xy",
    "positioning_resolution_z": "kg:positioning_resolution_z"
  },
  "@id": "kg:Industry_F340",
  "@type": "kg:Printer",
  "name": "Industry F340",
  "manufacturer": "3DGence",
  "type": [
    {
      "@id": "kg:FDM",
      "@type": "kg:print_technology"
    }
  ],
  "material": [
    {
      "@id": "kg:ABS",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:PLA",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:PA",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:ASA",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:PP",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:TPU",
      "@type": "kg:model_material"
    },
    {
      "@id": "kg:ESM-10",
      "@type": "kg:support_material"
    },
    {
      "@id": "kg:HIPS",
      "@type": "kg:support_material"
    },
    {
      "@id": "kg:BVOH",
      "@type": "kg:support_material"
    },
    {
      "@id": "kg:PA-CF",
      "@type": "kg:model_material"
    },
    {
      "@

```


</details>

<details>
<summary>Answer 4: &cross; interrupted data</summary>



```
{
  "@context": "https://schema.org",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": "3DGence",
  "printTechnology": "FFF",
  "workingTemperature": "15-32°C",
  "buildVolume": {
    "@type": "QuantitativeValue",
    "value": "26 520 cm3",
    "width": "260 mm",
    "height": "300 mm",
    "depth": "340 mm"
  },
  "storageTemperature": "0-32°C",
  "minLayerHeight": "40 μm",
  "nozzle": [
    {
      "@type": "QuantitativeValue",
      "name": "Printhead",
      "temperature": "500°C",
      "diameter": [
        "0.4 mm",
        "0.4 mm"
      ]
    },
    {
      "@type": "QuantitativeValue",
      "name": "HF",
      "temperature": "265°C",
      "diameter": [
        "0.6 mm",
        "0.6 mm"
      ],
      "modelMaterial": [
        "ABS",
        "ASA",
        "PA-CF",
        "PA-GF",
        "PA",
        "PP"
      ],
      "supportMaterial": [
        "ESM-10",
        "HIPS"
      ]
    },
    {
      "@type": "QuantitativeValue",
      "name": "HT",
      "temperature": "340°C",
      "diameter": [
        "0.4 mm",
        "0.4 mm"
      ],
      "modelMaterial": [
        "PC",
        "PC-ABS",
        "PC-ESD",
        "PC-CF"
      ],
      "supportMaterial": [
        "ABS",
        "ESM-10"
      ]
    },
    {
      "@type": "QuantitativeValue",
      "name": "HT",
      "temperature": "500°C",
      "diameter": [
        "max 0.4 mm",
        "0.4 mm"
      ],
      "modelMaterial": [
        "PEEK",
        "PEKK"
      ],
      "supportMaterial": [
        "ESM-10"
      ]
    }
  ],
  "filamentDiameter": "1.75 mm",
  "buildPlateTemperature": "160°C",
  "chamberTemperature": "85°C",
  "filamentChamberTemperature": "70°C",
  "maxPowerDraw": "2700 W",
  "powerRequirements": "230V AC",
  "communication": [
    "USB drive",
    "SD card"
  ],
  "slicingSoftware": "3DGence SLICER 4.0",
  "externalDimensions": {
    "@type": "QuantitativeValue",
    "value": "200 kg",
    "width": "1200 mm",
    "height": "800 mm",
    "depth": "1100 mm"
  },
  "construction": {
    "chassis": "powder coated steel",
    "filtration": "filtration unit",
    "upsDevice": "yes, optional",
    "buildSurface": "heated ceramic plate",
    "positioningResolutionXY": "0.006 mm",
    "positioningResolutionZ": "0.0004 mm"
  },
  "applications": [
    "Versatility",
    "Best printing results",
    "Job-specific printing modules",
    "Developed printing profiles"
  ],
  "

```


</details>






### ChatGPT 3.5 Mar 23 Version Round 2

<details>
<summary>Answer 1: &check; </summary>

```json-ld
{
  "@context": "https://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": "3DGence",
  "printingTechnology": "FFF",
  "buildVolume": "260 × 300 × 340 mm",
  "minLayerHeight": "40 μm",
  "numberOfPrintheads": 2,
  "nozzleDiameter": ["0.4/0.4 mm", "0.6/0.6 mm"],
  "filamentDiameter": "1.75 mm",
  "printheadTemperature": "500°C",
  "buildPlateTemperature": "160°C",
  "chamberTemperature": "85°C",
  "filamentChamberTemperature": "70°C",
  "communication": ["USB drive", "SD card"],
  "externalDimensions": "1200 × 800 × 1100 mm",
  "mass": "200 kg",
  "slicingSoftware": "3DGence SLICER 4.0",
  "filtration": "filtration unit",
  "chassis": "powder coated steel",
  "upsDevice": true,
  "buildSurface": "heated ceramic plate",
  "positioningResolutionXY": "0.006 mm",
  "positioningResolutionZ": "0.0004 mm",
  "materials": [
    {
      "@type": "Material",
      "name": "Pro",
      "maxTemperature": "265°C",
      "nozzleDiameter": "0.4 mm/0.4 mm",
      "modelMaterial": ["ABS", "PLA", "PA", "ASA", "PP", "TPU"],
      "supportMaterial": ["ESM-10", "HIPS", "BVOH"]
    },
    {
      "@type": "Material",
      "name": "HF",
      "maxTemperature": "265°C",
      "nozzleDiameter": "0.6 mm/0.6 mm",
      "modelMaterial": ["ABS", "ASA", "PA-CF", "PA-GF", "PA", "PP"],
      "supportMaterial": ["ESM-10", "HIPS"]
    },
    {
      "@type": "Material",
      "name": "HT",
      "maxTemperature": "340°C",
      "nozzleDiameter": "0.4 mm/0.4 mm",
      "modelMaterial": ["PC", "PC-ABS", "PC-ESD", "PC-CF"],
      "supportMaterial": ["ABS", "ESM-10"]
    },
    {
      "@type": "Material",
      "name": "HT",
      "maxTemperature": "500°C",
      "nozzleDiameter": "max 0.4 mm/0.4 mm",
      "modelMaterial": ["PEEK", "PEKK"],
      "supportMaterial": ["ESM-10"]
    }
  ],
  "applications": ["job-specific printing"],
  "technique": ["developed printing profiles"],
  "features": [
    "software access overdrive - remote shut down"
  ]
}
```
</details>


<details>
<summary>Answer 2: &cross; interrupted data </summary>


```{
"@context": "https://schema.org/",
"@type": "Printer",
"name": "Industry F340",
"manufacturer": {
"@type": "Organization",
"name": "3DGence"
},
"printerType": ["FFF"],
"material": [
{
"@type": "Material",
"name": "ABS",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "PLA",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "PA",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "ASA",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "PP",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "TPU",
"temperature": {
"@type": "Temperature",
"value": "Pro",
"maximum": "265°C"
},
"nozzleDiameter": "0.4/0.4 mm"
},
{
"@type": "Material",
"name": "ESM-10",
"temperature": {
"@type": "Temperature",
"value": "HF",
"maximum": "265°C"
},
"nozzleDiameter": "0.6/0.6 mm",
"supportMaterial": true
},
{
"@type": "Material",
"name": "HIPS",
"temperature": {
"@type": "Temperature",
"value": "HF",
"maximum": "265°C"
},
"nozzleDiameter": "0.6/0.6 mm",
"supportMaterial": true
},
{
"@type": "Material",
"name": "ABS",
"temperature": {
"@type": "Temperature",
"value": "HT",
"maximum": "340°C"
},
"nozzleDiameter": "0.4/0.4 mm",
"supportMaterial": true
},
{
"@type": "Material",
"name": "ASA",
"temperature": {
"@type": "Temperature",
"value": "HT",
"maximum": "340°C"
},
"nozzleDiameter": "0.4/0.4 mm",
"supportMaterial": false
},
{
"@type": "Material",
"name": "PA-CF",
"temperature": {
"@type": "Temperature",
```


</details>


<details>
<summary>Answer 3: &cross; interrupted data</summary>

```
{
"@context": "https://schema.org",
"@type": "Printer",
"name": "Industry F340",
"manufacturer": {
"@type": "Organization",
"name": "3DGence"
},
"printTechnology": ["FFF"],
"printingEnvironment": {
"@type": "PrintingEnvironment",
"workingTemperature": {
"@type": "Temperature",
"minValue": 15,
"maxValue": 32,
"unitCode": "CEL"
},
"storageTemperature": {
"@type": "Temperature",
"minValue": 0,
"maxValue": 32,
"unitCode": "CEL"
},
"minLayerHeight": {
"@type": "Distance",
"value": 40,
"unitCode": "MICRO_M"
},
"numberOfPrintheads": 2,
"nozzleDiameter": ["0.4/0.4 mm", "0.6/0.6 mm"],
"filamentDiameter": {
"@type": "Distance",
"value": 1.75,
"unitCode": "MM"
},
"chamberTemperature": {
"@type": "Temperature",
"value": 85,
"unitCode": "CEL"
},
"filamentChamberTemperature": {
"@type": "Temperature",
"value": 70,
"unitCode": "CEL"
},
"communication": ["USB drive", "SD card"]
},
"power": {
"@type": "Power",
"printheadTemperature": {
"@type": "Temperature",
"value": 500,
"unitCode": "CEL"
},
"buildplateTemperature": {
"@type": "Temperature",
"value": 160,
"unitCode": "CEL"
},
"powerRequirements": "230V AC",
"maxPowerDraw": {
"@type": "Energy",
"value": 2700,
"unitCode": "WATT"
}
},
"dimensionsAndMass": {
"@type": "DimensionsAndMass",
"externalDimensions": {
"@type": "Distance",
"value": {
"width": 1200,
"height": 800,
"depth": 1100
},
"unitCode": "MM"
},
"mass": {
"@type": "Mass",
"value": 200,
"unitCode": "KG"
}
},
"safety": {
"@type": "Safety",
"filtration": "filtration unit",
"chassis": "powder coated steel",
"UPSDevice": true,
"buildSurface": "heated ceramic plate",
"others": [
"software access overdrive - remote shutdown"
]
},
"versatility": {
"@type": "Versatility",
"printingModules": [
{
"@type": "PrintingModule",
"temperature": "PRO",
"maxTemperature": {
"@type": "Temperature",
"value": 265,
"unitCode": "CEL"
},
"nozzleDiameter": "0.4 mm/0.4 mm",
"modelMaterial": [
"ABS",
"PLA",
"PA",
"ASA",
"PP",
"TPU"
],
"supportMaterial": [
"ESM-10",
"HIPS",
"BVOH"

```

</details>


<details>
<summary>Answer 4: &cross; interrupted data</summary>


```
{
  "@context": "https://schema.org",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": {
    "@type": "Organization",
    "name": "3DGence"
  },
  "printTechnology": [
    "FFF"
  ],
  "workingTemperature": "15-32°C",
  "buildVolume": {
    "@type": "Dimensions",
    "width": "260mm",
    "height": "300mm",
    "depth": "340mm",
    "volume": "26,520cm3"
  },
  "storageTemperature": "0-32°C",
  "minLayerHeight": "40μm",
  "numberOfPrintheads": 2,
  "printheadSpecifications": [
    {
      "@type": "PrintheadSpecification",
      "nozzleDiameter": [
        "0.4mm",
        "0.4mm"
      ],
      "filamentDiameter": "1.75mm",
      "temperature": "500°C"
    },
    {
      "@type": "PrintheadSpecification",
      "nozzleDiameter": [
        "0.6mm",
        "0.6mm"
      ],
      "filamentDiameter": "1.75mm",
      "temperature": "265°C"
    },
    {
      "@type": "PrintheadSpecification",
      "nozzleDiameter": [
        "0.4mm",
        "0.4mm"
      ],
      "filamentDiameter": "1.75mm",
      "temperature": "340°C"
    },
    {
      "@type": "PrintheadSpecification",
      "nozzleDiameter": [
        "max 0.4mm",
        "0.4mm"
      ],
      "filamentDiameter": "1.75mm",
      "temperature": "500°C"
    }
  ],
  "powerSpecifications": {
    "@type": "PowerSpecifications",
    "printheadTemperature": "500°C",
    "buildPlateTemperature": "160°C",
    "chamberTemperature": "85°C",
    "maxPowerDraw": "2700W",
    "filamentChamberTemperature": "70°C",
    "communication": [
      "USB drive",
      "SD card"
    ],
    "powerRequirements": "230V AC"
  },
  "dimensions": {
    "@type": "Dimensions",
    "width": "1200mm",
    "height": "800mm",
    "depth": "1100mm",
    "mass": "200kg"
  },
  "slicingSoftware": "3DGence SLICER 4.0",
  "filtration": "filtration unit",
  "chassis": "powder coated steel",
  "upsDevice": true,
  "buildSurface": "heated ceramic plate",
  "positioningResolutionXY": "0.006mm",
  "positioningResolutionZ": "0.0004mm",
  "materialSpecifications": [
    {
      "@type": "MaterialSpecification",
      "name": "PRO",
      "modelMaterial": [
        "ABS",
        "PLA",
        "PA",
        "ASA",
        "PP",
        "TPU"
      ],
      "supportMaterial": [
        "ESM-10",
        "HIPS",
        "BVOH"
      ],
      "temperature": "up to 265°C",
      "nozzleDiameter": [
        "0.4mm",

```


</details>

<details>
<summary>Answer 5: &cross; interrupted data</summary>

```{
  "@context": "http://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": {
    "@type": "Organization",
    "name": "3DGence"
  },
  "printTechnology": [
    "FFF"
  ],
  "buildVolume": {
    "@type": "Dimensions",
    "width": "260mm",
    "height": "300mm",
    "depth": "340mm",
    "volume": "26,520cm³"
  },
  "minLayerHeight": "40μm",
  "printhead": {
    "@type": "Printhead",
    "count": 2,
    "nozzleDiameter": [
      "0.4mm",
      "0.4mm",
      "0.6mm",
      "0.6mm"
    ],
    "filamentDiameter": "1.75mm"
  },
  "temperature": {
    "@type": "Temperature",
    "workingTemperature": "15-32°C",
    "chamberTemperature": "85°C (active heating)",
    "filamentChamberTemperature": "70°C",
    "printheadTemperature": "500°C",
    "buildPlateTemperature": "160°C"
  },
  "power": {
    "@type": "Power",
    "powerRequirements": "230V AC",
    "maxPowerDraw": "2700W"
  },
  "communication": [
    "USB drive",
    "SD card"
  ],
  "dimensionsAndMass": {
    "@type": "DimensionsAndMass",
    "externalDimensions": {
      "@type": "Dimensions",
      "width": "1200mm",
      "height": "800mm",
      "depth": "1100mm"
    },
    "mass": "200kg"
  },
  "slicingSoftware": "3DGence SLICER 4.0",
  "filtration": "filtration unit",
  "chassis": "powder coated steel",
  "upsDevice": "yes, optional",
  "buildSurface": "heated ceramic plate",
  "positioningResolution": {
    "@type": "PositioningResolution",
    "XY": "0.006mm",
    "Z": "0.0004mm"
  },
  "materials": [
    {
      "@type": "Material",
      "name": "PRO",
      "temperature": "up to 265°C",
      "nozzleDiameter": "0.4mm/0.4mm",
      "modelMaterial": [
        "ABS",
        "PLA",
        "PA",
        "ASA",
        "PP",
        "TPU"
      ],
      "supportMaterial": [
        "ESM-10",
        "HIPS",
        "BVOH"
      ]
    },
    {
      "@type": "Material",
      "name": "HF",
      "temperature": "up to 265°C",
      "nozzleDiameter": "0.6mm/0.6mm",
      "modelMaterial": [
        "ABS",
        "ASA",
        "PA-CF",
        "PA-GF",
        "PA",
        "PP"
      ],
      "supportMaterial": [
        "ESM-10",
        "HIPS"
      ]
    },
    {
      "@type": "Material",
      "name": "HT",
      "temperature": "up to 340°C",
      "nozzleDiameter": "0

```


</details>




### GPT-3.5 turbo playground 


<details>
<summary>Answer 1: &check;</summary>



```
{
  "@context": "https://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": {
    "@type": "Organization",
    "name": "3DGence"
  },
  "printTechnology": ["FFF", "SLA", "SLS"],
  "material": [
    {
      "@type": "Material",
      "name": "ABS",
      "temperature": ["PRO up to 265°C", "HF up to 265°C", "HT up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "PLA",
      "temperature": ["PRO up to 265°C"]
    },
    {
      "@type": "Material",
      "name": "PA",
      "temperature": ["PRO up to 265°C", "HF up to 265°C"]
    },
    {
      "@type": "Material",
      "name": "ASA",
      "temperature": ["PRO up to 265°C", "HF up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "PP",
      "temperature": ["PRO up to 265°C", "HF up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "TPU",
      "temperature": ["PRO up to 265°C"]
    },
    {
      "@type": "Material",
      "name": "PA-CF",
      "temperature": ["HF up to 265°C"]
    },
    {
      "@type": "Material",
      "name": "PA-GF",
      "temperature": ["HF up to 265°C"]
    },
    {
      "@type": "Material",
      "name": "PC",
      "temperature": ["HT up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "PC-ABS",
      "temperature": ["HT up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "PC-ESD",
      "temperature": ["HT up to 340°C"]
    },
    {
      "@type": "Material",
      "name": "PEEK",
      "temperature": ["HT up to 500°C"]
    },
    {
      "@type": "Material",
      "name": "PEKK",
      "temperature": ["HT up to 500°C"]
    },
    {
      "@type": "Material",
      "name": "ESM-10",
      "supportMaterial": true
    },
    {
      "@type": "Material",
      "name": "HIPS",
      "supportMaterial": true
    },
    {
      "@type": "Material",
      "name": "BVOH",
      "supportMaterial": true
    }
  ],
  "applications": ["job-specific printing"],
  "technique": ["developed printing profiles"],
  "printingEnvironment": {
    "workingTemperature": "15-32°C",
    "buildVolume": "260 × 300 × 340 mm (26 520 cm3)",
    "storageTemperature": "0-32°C",
    "minLayerHeight": "40 μm",
    "numberOfPrintheads": "2 per module",
    "nozzleDiameter": ["0.4/0.4 mm", "0.6/0.6 mm"],
    "filamentDiameter": "1.75 mm",
    "printheadTemperature": "500°C",
    "buildplateTemperature": "160°C",
    "chamberTemperature": "85°C (active heating)",
    "filamentChamberTemperature": "70°C",
    "communication": ["USB drive", "SD card"],
    "powerRequirements": "230V AC",
    "maxPowerDraw": "2700 W"
  },
  "dimensionsAndMass": {
    "externalDimensions": "1200 × 800 × 1100 mm",
    "mass": "200 kg"
  },
  "safety": {
    "filtration": "filtration unit",
    "chassis": "powder coated steel",
    "upsDevice": true,
    "buildSurface": "heated ceramic plate",
    "others": ["software access overdrive - remote shut down"],
    "positioningResolutionXY": "0.006 mm",
    "positioningResolutionZ": "0.0004 mm"
  },
  "slicingSoftware": "3DGence SLICER 4.0"
}
```


</details>


<details>
<summary>Answer 2: &cross; no data</summary>



```
Note: This JSON_LD formatted Knowledge Graph is based on the information provided in the original text. Some additional information or clarification may be required for a more complete and accurate representation of the 3DGence 3d printer specification.
```


</details>


<details>
<summary>Answer 3: &cross; no data </summary>



```
As an AI language model, I cannot browse the internet or access external information beyond the text provided. Therefore, I have created the KG based solely on the information provided in the original text.
```


</details>


<details>
<summary>Answer 4: &check;</summary>

Here's the updated JSON_LD formatted Knowledge Graph with the missing information:

```
{
  "@context": "https://schema.org/",
  "@type": "Printer",
  "name": "Industry F340",
  "manufacturer": {
    "@type": "Organization",
    "name": "3DGence"
  },
  "printTechnology": ["FFF"],
  "material": [
    {
      "@type": "Material",
      "name": "ABS",
      "temperature": ["PRO up to 265°C", "HF up to 265°C", "HT up to 340°C"],
      "supportMaterial": ["ESM-10", "HIPS", "BVOH"]
    },
    {
      "@type": "Material",
      "name": "PLA",
      "temperature": ["PRO up to 265°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PA",
      "temperature": ["PRO up to 265°C", "HF up to 265°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "ASA",
      "temperature": ["PRO up to 265°C", "HF up to 340°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PP",
      "temperature": ["PRO up to 265°C", "HF up to 340°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "TPU",
      "temperature": ["PRO up to 265°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PA-CF",
      "temperature": ["HF up to 265°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PA-GF",
      "temperature": ["HF up to 265°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PC",
      "temperature": ["HT up to 340°C"],
      "supportMaterial": ["ABS", "ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PC-ABS",
      "temperature": ["HT up to 340°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PC-ESD",
      "temperature": ["HT up to 340°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PEEK",
      "temperature": ["HT up to 500°C"],
      "supportMaterial": ["ESM-10"]
    },
    {
      "@type": "Material",
      "name": "PEKK",
      "temperature": ["HT up to 500°C"],
      "supportMaterial": ["ESM-10"]
    }
  ],
  "applications": ["job-specific printing"],
  "technique": ["developed printing profiles"],
  "printingEnvironment": {
    "workingTemperature": "15-32°C",
    "buildVolume": "260 × 300 × 340 mm (26 520 cm3)",
    "storageTemperature": "0-32°C",
    "minLayerHeight": "40 μm",
    "numberOfPrintheads": "2 per module",
    "nozzleDiameter": ["0.4/0.4 mm", "0.6/0.6 mm"],
    "filamentDiameter": "1.75 mm",
    "printheadTemperature": "500°C",
    "buildplateTemperature": "160°C",
    "chamberTemperature": "85°C (active heating)",
    "filamentChamberTemperature": "70°C",
    "communication": ["USB drive", "SD card"],
    "powerRequirements": "230V AC",
    "maxPowerDraw": "2700 W"
  },
  "dimensionsAndMass": {
    "externalDimensions": "1200 × 800 × 1100 mm",
    "mass": "200 kg"
  },
  "safety": {
    "filtration": "filtration unit",
    "chassis": "powder coated steel",
    "upsDevice": true,
    "buildSurface": "heated ceramic plate",
    "others": ["software access overdrive - remote shut down"],
    "positioningResolutionXY": "0.006 mm",
    "positioningResolutionZ": "0.0004 mm"
  },
  "slicingSoftware": "3DGence SLICER 4.0"
}
```


</details>





