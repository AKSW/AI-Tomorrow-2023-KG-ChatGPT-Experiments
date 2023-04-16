# 3d printer


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


### ChatGPT 3.5 Mar 23 Version

<details>
<summary>Answer 1/5: &check; </summary>

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
<summary>Answer 2/5: &cross; interrupted data </summary>


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
<summary>Answer 3/5: &cross; interrupted data</summary>

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
<summary>Answer 4/5: &cross; </summary>


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
<summary>Answer 5/5: &check;</summary>


```

```


### GPT-3.5 turbo playground Mar 23 Version

<details>
<summary>Answer 1/5: &check;</summary>



```
```


</details>


