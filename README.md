# Create Project Using the IWIN AT Commands
### LINK: https://os.mbed.com/teams/ST/code/DISCO_L475VG_IOT01-wifi-client/ \
![image](https://user-images.githubusercontent.com/54381052/158496865-9c20b71d-1e04-4fcc-af04-8ee8ebcbbf47.png)


``` cpp
// FILE NAME: es_wifi.c LINE:814
ES_WIFI_Status_t ES_WIFI_Connect(ES_WIFIObject_t *Obj, const char* SSID, const char* Password, ES_WIFI_SecurityType_t SecType)
{
  ES_WIFI_Status_t ret;
 
  sprintf((char*)Obj->CmdData,"C1=%s\r", SSID);  //C1 = NetworkName 
  ret = AT_ExecuteCommand(Obj, Obj->CmdData, Obj->CmdData);
  if(ret == ES_WIFI_STATUS_OK)
  {
    sprintf((char*)Obj->CmdData,"C2=%s\r", Password);  //C2 = password 
    ret = AT_ExecuteCommand(Obj, Obj->CmdData, Obj->CmdData);
   
    if(ret == ES_WIFI_STATUS_OK)
    {
      Obj->Security = SecType;
      sprintf((char*)Obj->CmdData,"C3=%d\r", (uint8_t)SecType);  //C3 = WPA2 
      ret = AT_ExecuteCommand(Obj, Obj->CmdData, Obj->CmdData);
     
      if(ret == ES_WIFI_STATUS_OK)
      {
        sprintf((char*)Obj->CmdData,"C0\r");  //C0
        ret = AT_ExecuteCommand(Obj, Obj->CmdData, Obj->CmdData);  
        if(ret == ES_WIFI_STATUS_OK)
        {
           Obj->NetSettings.IsConnected = 1;
        }
      }    
    }
  }
```

![image](https://user-images.githubusercontent.com/54381052/156871303-afe0b29e-465b-4939-aaaa-0a792e59bb2e.png)

### Use UART
``` cpp
// FILE: es_wifi_conf.h LINE:77
#define ES_WIFI_USE_SPI                             0    
#define ES_WIFI_USE_UART                            (!ES_WIFI_USE_SPI)
```

# Important 
  * Have Stlink on your host PC prior to installing the ```EsWiFi``` Demo APP.
  * ``` C:\Program Files (x86)\STMicroelectronics\STM32 ST-LINK Utility\ST-LINK Utility ```
# Streaming Mode C code
  * https://www.inventeksys.com/iwin/streaming-mode-c-code/

# Inventek IWIN AT Commands (ES-WiFi)
  Main web page: https://www.inventeksys.com/es-wifi-support/
# Init Setup
  Baudrate 115k or 115200
  Bin File Provided:\
  https://github.com/Firefighter-Mesh-Network-UNM-UTD/ISM-Inventek-IWIN-AT-Commands/blob/main/ISM43362_M3G_L44_C6.2.1.11%5B1%5D.bin \
  Oficial site:
  https://www.inventeksys.com/iwin/firmware/ 
# P2P 1:1 and UDP Setup
![image](https://user-images.githubusercontent.com/54381052/156871284-4c14297c-50bb-405c-962b-b112a0f049a1.png)

![image](https://user-images.githubusercontent.com/54381052/156871303-afe0b29e-465b-4939-aaaa-0a792e59bb2e.png)
 
 ![image](https://user-images.githubusercontent.com/54381052/156871314-90d290df-3db1-4e9d-96b1-5b338436ab9c.png)

# Wi-Fi Direct 
``` AD ``` Activate AP Direct Connect Mode \
\
![image](https://user-images.githubusercontent.com/54381052/156871434-45f130dc-d9a8-4265-9e84-25f8a91cae57.png)

![image](https://user-images.githubusercontent.com/54381052/156871332-fe1791e2-bfaa-48bc-b4e0-378d04372c1e.png)
