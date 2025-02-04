| **Parameter**                 | **Default value**                       | **Description**                                                                                                               |
|:-|:-|-
| deviceName                    | **Gateway**                             | Device name                                                                                                                   |
| deviceType                    | **default**                             | Device type                                                                                                                   |
| type                          | **tcp**                                 | Type of connection may be **tcp**, **udp** or **serial**.                                                                     |
| host                          | **127.0.0.1**                           | Hostname or ip address of Modbus server.                                                                                      |
| port                          | **5020**                                | Port of Modbus server for connect.                                                                                            |
| method                        | **socket**                              | Type of framer **socket** or **rtu**, if needed.                                                                              |
| byteOrder                     | **BIG**                                 | Order of bytes to read.                                                                                                       |
| unitId                        | **0**                                   | Unit id of the device                                                                                                         |
| pollPeriod                    | **5000**                                | Period in milliseconds for check the attributes and the telemetry.                                                            |
| sendDataToThingsBoard         | **false**                               | If set to TRUE, Gateway make autoconfiguration and every <pollPeriod> ms send values to ThingsBoard                           |
|---
