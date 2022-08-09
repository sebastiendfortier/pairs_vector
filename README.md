# Vector data ingestion into pairs


## Pairs table format

time (unix epoch utc), lat, lon, layer1, layer2, layerX.., dimension1, dimensionX..., property1, propertyX...

## Primary key composition
  
Always, time, lat, lon and dimensions.    

You must make sure that each row in the csv file is unique on those criterias.    


## Pairs ingest file types

### CSV

The specification of the csv file is simple.   

- No index
- No header
- time, lat, lon, followed by layer columns , dimension columns and finally property columns

### meta

- Refer to ingest.met for contents.   
- All csv files must be accompnied by a .meta file of the same name as the csv file



# File descriptions

## schema

File containing a sample row to be inserted in the database.    

## dset.json

Contains the metadata for creating the dataset that will hold layers, dimensions and properties in the pairs database.    

## dlayers.json

Contains the metadata for creating the layers event_strenght, chi_squared_value, semi_major_axis, semi_minor_axis, angle_of_the_confidence, flash_event_multiplicity  in the pairs database.     
It is associated with the corresponding columns in the schema file.    

## dim1.json

Contains the metadata for creating the dimension cgstatus in the pairs database.      
It is associated with the corresponding column in the schema file.      


## prop.json

Contains the metadata for creating the property eventtime in the pairs database.    
It is associated with the corresponding column in the schema file.   


## ingest.meta

This is the template file that accompanies every csv file to be ingested.    

Ex.: 12345.csv will have 12345.meta so that the pairs uploader knows to ingest that csv and where to ingest it into   

- pairsdataset=real-time-lightning-events-ca
name of the created dataset in pairs
- pairsdatatable=lightning-records
name of the created table to ingest in pairs database
- uploadpriority=5
check the pairs api
- pairsdatatype=point
indicates that this is point data

