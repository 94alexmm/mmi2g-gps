# Reverse engineering the Audi MMI 2G Navigation disc


## File structure
.DB or .DB_ extensions refer to FLDB format database. This is a propitiatory archive format specific to Harman Becker navigation discs.

Examples of Harman Becker navigation systems include BMW CCC/iDrive, Audi MMI and Mercedes NTG.

## Archive contents
Depending on the map disc age/location/contents the files on the disc can vary slightly.
<img width="626" alt="image" src="https://github.com/94alexmm/mmi2g-gps/assets/15701642/5345669e-ceac-4b20-8ac0-d94c239c5310">
<img width="848" alt="image" src="https://github.com/94alexmm/mmi2g-gps/assets/15701642/81bd469c-8d22-4dce-8d04-adfcc9ecf91f">
<img width="920" alt="image" src="https://github.com/94alexmm/mmi2g-gps/assets/15701642/eb90d29d-5163-415c-baf9-b2fc5457640c">

## Optional RDS TMC Data
This is only present on regions that have RDS TMC
<img width="919" alt="image" src="https://github.com/94alexmm/mmi2g-gps/assets/15701642/6ab21736-76ff-4539-b1fa-29b1e16b6eaf">

# Inside the XAC/POI Archive
XAH file appears to be header for whole DB file. It makes reference to all the XAC files by name, followed by 80 unknown bytes.
<img width="768" alt="image" src="https://github.com/94alexmm/mmi2g-gps/assets/15701642/0f351de9-22db-4cf9-bdd0-6767d63f8efe">

## PLZ file
Something to do with postcodes, given german translation. Not much in here, mostly 0s.
![image](https://github.com/94alexmm/mmi2g-gps/assets/15701642/dcfc47b1-0131-4fc5-8c58-779ee68dc976)

## .B files / .V files
Looks very similar to XAC file contents but has header “SMART XAC” instead
![image](https://github.com/94alexmm/mmi2g-gps/assets/15701642/f467ec03-3fc8-4318-806a-e97d8c3fae9c)

##.ORT Files
Translates to place names. Looks compressed based on truncated recognisable town names.
![image](https://github.com/94alexmm/mmi2g-gps/assets/15701642/4568c89b-4d52-4ecc-a020-f8b59e0fc4b9)

#Attempt at repackage of new maps to old CD format
Create new FLDB with same name but include only new GDB. Starts up fine, but maps screen just stays black. Didnt show any new roads only old set. Assuming this means GDB doesnt have road names.
