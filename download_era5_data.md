# download climate data of era5 using python on linux

## 1 install the CDS API KEY
1. register an account at CDS registration page  and log in 
2. copy the code displayed beside, in the file **$HOME/.cdsapirc**

## 2 install the CDS API client
The CDS API client is a python based library

install the CDS API via pip, by running

```
$ pip install cdsapi
```

## 3 use the CDS API client for data access

Attached to each dataset download form, the following button displays the python code to be used. 
The request can be formatted using the interactive form. 

The api call must follow the syntax

```python   
import cdsapi
c = cdsapi.Client()

c.retrieve('dataset-short-names',
            {...sub-selection request...},
            'target-file')
```

**example**
```python
#!/usr/bin/env python
import cdsapi
c = cdsapi.Client()
c.retrieve("reanalysis-era5-pressure-levels",
    {
        "variable": "temperature",
        "pressure_level": "1000",
        "product_type": "reanalysis",
        "year": "2008",
        "month": "01",
        "day": "01",
        "time": "12:00",
        "format": "grib"
    }, "download.grib")
```


