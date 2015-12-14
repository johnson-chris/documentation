####A collection of notes on how to setup a new FC initiator on a Cisco NX-OS switch


####Check for exisiting fabric logins for new pwwn
`N5K-A# show flogi database`


####You can also filter these results for example this only includes fabric logins over San-po100


```
N5K-A# show flogi database | inc San-po104
San-po100        1     0xa0001a  24:68:00:2a:6a:73:8b:00 20:01:00:2a:6a:73:8b:01
San-po100        1     0xa0001b  20:00:00:25:b5:0a:00:0f 20:00:00:25:b5:ff:00:0f
San-po100        1     0xa0001d  20:00:00:25:b5:0a:00:0e 20:00:00:25:b5:ff:00:0e
San-po100        1     0xa0001e  20:00:00:25:b5:0a:00:0d 20:00:00:25:b5:ff:00:0d
San-po100        1     0xa0001f  20:00:00:25:b5:0a:00:0c 20:00:00:25:b5:ff:00:0c
```


####Check for device alias
`N5K-A# show device-alias database`

####Set a device alias for a new wwpn

#####Enter global configuration mode
`N5K-A# configure terminal`

####Enter the device alias configuration section
`N5K-A(config)#device-alias database`

#####Create the device-alias name to pwwn mapping
`N5K-A(config-device-alias-db)# device-alias name "hostname-adapter-fabric" pwww "enter pwwn from flogi or pull from ucs service profile etc"`

#####Commit the device alias to the switch and exit the device alias configuration section
`N5K-A(config-device-alias-db)# device-alias commit`
`N5K-A(config-device-alias-db)# exit`

#####Create a zone for the new host
`N5K-A(config)# zone name 'hostname-fabricid' vsan 'vsan id'`


#####Example
`N5K-A(config)# zone name esx01-fabricA vsan 1`

#####You can then add members to the zone you will be in the zone configuration section
`N5K-A(config-zone)# member device-alias "device-alias we just created"`
#####Or you can use the pwwn of the device if you dont want to zone off the device-alias name
`N5K-A(config-zone)# member pwwn "pwwn of host"`
`N5K-A(config-zone)# member pwwn "pwwn of storage target"`


#####You can also zone by device-alias name (I am thinking about converting to using this in the future)
`N5K-A(config-zone)# member device-alias "device-alias name"`

#####Add the zone to exisiting zoneset or create a new one
`N5K-A(config)# zoneset name "zone-fabric name" vsan "vsan id"`

#####Example
`N5K-A(config)# zoneset name vsphere-fabricA vsan 1`
`N5K-A(config-zoneset)# member esx01-fabricA`

#####Check the exisitng zoneset configuration
`N5K-A#show zoneset`

#####Check the exisiting active zonesets
`N5K-A#show zoneset active`

#####To effect the fabric change you will need to enable the zoneset
`N5K-A(config)# zoneset activate name "zoneset name" vsan "vsanid"`
