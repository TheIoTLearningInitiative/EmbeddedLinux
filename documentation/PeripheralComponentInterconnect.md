Peripheral Component Interconnect
==


> Conventional PCI, often shortened to PCI, is a local computer bus for attaching hardware devices in a computer. PCI is the initialism for Peripheral Component Interconnect[2] and is part of the PCI Local Bus standard. The PCI bus supports the functions found on a processor bus but in a standardized format that is independent of any particular processor's native bus. Devices connected to the PCI bus appear to a bus master to be connected directly to its own bus and are assigned addresses in the processor's address space. It is a parallel bus, synchronous to a single bus clock. Wikipedia

- [Wikipedia Peripheral Component Interconnect](https://es.wikipedia.org/wiki/Peripheral_Component_Interconnect)

```sh
    root@edison:~# lspci
    00:00.0 Host bridge: Intel Corporation Device 1170 (rev 01)             
    00:01.0 SD Host controller: Intel Corporation Device 1190 (rev 01)      
    00:01.2 SD Host controller: Intel Corporation Device 1190 (rev 01)      
    00:01.3 SD Host controller: Intel Corporation Device 1190 (rev 01)         
    00:02.0 Display controller: Intel Corporation Device 1182 (rev 01)         
    00:04.0 Serial controller: Intel Corporation Device 1191 (rev 01)          
    00:04.1 Serial controller: Intel Corporation Device 1191 (rev 01)           
    00:04.2 Serial controller: Intel Corporation Device 1191 (rev 01)           
    00:04.3 Serial controller: Intel Corporation Device 1191 (rev 01)           
    00:05.0 Serial controller: Intel Corporation Device 1192 (rev 01)           
    00:06.0 System peripheral: Intel Corporation Device 1193 (rev 01)           
    00:06.1 System peripheral: Intel Corporation Device 1193 (rev 01)           
    00:07.0 System peripheral: Intel Corporation Device 1194 (rev 01)           
    00:07.1 System peripheral: Intel Corporation Device 1194 (rev 01)           
    00:07.2 System peripheral: Intel Corporation Device 1194 (rev 01)           
    00:08.0 Communication controller: Intel Corporation Device 1195 (rev 01)    
    00:08.1 Communication controller: Intel Corporation Device 1195 (rev 01)    
    00:08.2 Communication controller: Intel Corporation Device 1195 (rev 01)    
    00:08.3 Communication controller: Intel Corporation Device 1195 (rev 01)    
    00:09.0 Communication controller: Intel Corporation Device 1196 (rev 01)    
    00:09.1 Communication controller: Intel Corporation Device 1196 (rev 01)    
    00:09.2 Communication controller: Intel Corporation Device 1196 (rev 01)    
    00:0a.0 Communication controller: Intel Corporation Device 1197 (rev 01)    
    00:0b.0 Encryption controller: Intel Corporation Device 1198 (rev 01)       
    00:0c.0 System peripheral: Intel Corporation Device 1199 (rev 01)           
    00:0d.0 Multimedia audio controller: Intel Corporation Device 119a (rev 01) 
    00:0e.0 System peripheral: Intel Corporation Device 119b (rev 01)           
    00:11.0 USB controller: Intel Corporation Device 119e (rev 01)              
    00:12.0 Signal processing controller: Intel Corporation Device 119f (rev 01)
    00:13.0 Co-processor: Intel Corporation Device 11a0 (rev 01)                
    00:14.0 Co-processor: Intel Corporation Device 11a1 (rev 01)                
    00:15.0 System peripheral: Intel Corporation Device 11a2 (rev 01)           
    00:16.0 Co-processor: Intel Corporation Device 11a3 (rev 01)                
    00:16.1 Co-processor: Intel Corporation Device 11a4 (rev 01)                
    00:17.0 System peripheral: Intel Corporation Device 11a5 (rev 01)           
    00:18.0 Display controller: Intel Corporation Device 11a6 (rev 01)
    root@ubilinux:~# cat /proc/bus/pci/devices
```

## Links

- https://communities.intel.com/thread/61150?wapkw=intel+edison+mpcie
- https://communities.intel.com/thread/89971?start=0&tstart=0
- https://www.aisler.net/projects/7252
- http://pinball-mods.com/blogs/?p=580
- https://hackaday.io/project/4571-intel-edison-usb-storage-sled
- https://wiki.archlinux.org/index.php/Huawei_E220
- https://techship.se/products/mpcie-usb-adapt-9-pin/
- https://techship.se/products/pci-express-mini-card-to-usb-adapter/
- https://techship.se/products/pci-express-mini-card-to-usb-adapter-with-external-voltage/
- http://www.amazon.com/Mini-PCIe-mSATA-Micro-Adapter/dp/B00KZIANT0
- http://www.newegg.com/Product/Product.aspx?Item=N82E16815158354
