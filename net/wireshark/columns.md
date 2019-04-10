# Wireshark Columns

#### Delta between packet timestamps (all tcp packets)
Add New columens  
Edit -> Prefrences -> Appearance -> Columns -> +  
Change Title to Delta and Type to Delta Time

#### Delta between packet timestamps (relative to tcp stream)
click on any tcp packet  
rigth click Transmission Control Protocol and enable Protocol Preferences -> Calculate converstion timestamps  
right click (inside Transmission Control Protocol) on timestamps -> Time since previous frame in this tcp stream
 and click apply as column  
change the column name in Edit -> Prefrences -> Appearance -> Columns 