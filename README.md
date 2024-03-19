# Data Processing for ROSE

Four datasets can be processed:

* InSAR provided by Sensar
* RILA provided by Fugro
* Inframon provided by Ricardo
* SoS provided by Deltares

The InSAR, RILA and Inframon datasets are closed source. The SoS dataset is open source.

# Process the data

## InSAR
To process the InSAR dataset you can use [sensar.py](/data_proc/sensar.py).
This script will process the InSAR dataset and output a pickle file with the processed data.

Alternatively, you can use the following code to process the InSAR dataset:

```python
from data_proc.sensar import read_geopackage, save_sensar_data

data = read_geopackage(r"./data/Sensar/20190047_02_20210630/data/data.gpkg")
save_sensar_data(data, "./insar_data.pickle")
```



## RILA
To process the RILA dataset you can use [fugro.py](/data_proc/fugro.py).
This script will process the RILA dataset and output a pickle file with the processed data.

Alternatively, you can use the following code to process the RILA dataset:

```python
from data_proc.fugro import get_data_at_location, save_fugro_data

res = get_data_at_location(r"./data/Fugro/Amsterdam-Eindhoven TKI Project", location="all")
save_fugro_data(res, r"./rila_data.pickle")
```

## Inframon
To process the Inframon dataset you can use [ricardo.py](/data_proc/ricardo.py).
This script will process the Inframon dataset and output a pickle file with the processed data.

Alternatively, you can use the following code to process the Inframon dataset:

```python
from data_proc.ricardo import read_inframon

filenames = [r"./data/Ricardo/Jan.json",
                r"./data/Ricardo/Jun.json",
                ]
read_inframon(filenames, "./inframon.pickle")
```

## SoS
To process the SoS dataset you can use [SoS.py](/data_proc/SoS.py).
This script will process the SoS dataset and output a Json file with the processed data, and plot the SoS scenarios.

Alternatively, you can use the following code to process the SoS dataset:

```python
from data_proc.SoS import ReadSosScenarios

sos = ReadSosScenarios("data/SoS/soilprofiles.csv", "data/SoS/20201102_Prorail_parameters_SOS.csv",
                        "data/SoS/segments.csv", "data/SoS/Segments_TKI_v2.shp")
sos.create_segments()
sos.dump("./SOS.json")
sos.plot_sos(output_folder="./SOS/results")
```
