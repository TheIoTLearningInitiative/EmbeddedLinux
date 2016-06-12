# Reboot

```sh
root@edison:~# reboot
         Unmounting /home...
         Stopping User Manager for UID 0...
         Stopping Hostname Service...
         Stopping Bluetooth service...
         Stopping Redis Server...
         Stopping Watchdog sample daemon...
         Starting Store Sound Card State...
[  OK  ] Stopped Watchdog sample daemon.                                        
[  OK  ] Stopped Bluetooth service.                                             
[  OK  ] Stopped Hostname Service.                                              
[  OK  ] Stopped Serial Getty on ttyMFD2.                                       
[  OK  ] Stopped The Edison status and configuration service.                   
[  OK  ] Stopped User Manager for UID 0.                                        
[  OK  ] Unmounted /home.                                                       
[  OK  ] Stopped Redis Server.                                                  
[  OK  ] Started Store Sound Card State.                                        
[  OK  ] Removed slice user-0.slice.                                            
[  OK  ] Stopped target Multi-User System.                                      
         Stopping Edison PWR button handler...                                  
         Unmounting Mount for factory...                                        
         Stopping Mosquitto - lightweight server implementati...SN protocols... 
         Stopping Intel_XDK_Daemon...                                           
         Stopping Network Name Resolution...                                    
         Stopping PulseAudio Sound System...                                    
         Stopping Telephony service...                                          
         Stopping Daemon to reset sketches...                                   
         Stopping OpenSSH Key Generation...                                     
[  OK  ] Stopped OpenSSH Key Generation.                                        
         Stopping Bluetooth rf kill event daemon...                             
         Stopping Login Service...                                              
         Stopping D-Bus System Message Bus...                                   
[  OK  ] Stopped target Login Prompts.                                          
         Stopping Getty on tty1...                                              
[  OK  ] Removed slice system-serial\x2dgetty.slice.                            
[  OK  ] Stopped Edison PWR button handler.                                     
[  OK  ] Stopped Telephony service.                                             
[  OK  ] Stopped Bluetooth rf kill event daemon.                                
[  OK  ] Stopped Daemon to reset sketches.                                      
[  OK  ] Stopped Login Service.                                                 
[  OK  ] Stopped D-Bus System Message Bus.                                      
[  OK  ] Stopped PulseAudio Sound System.                                       
[  OK  ] Stopped Network Name Resolution.                                       
[  OK  ] Stopped Getty on tty1.                                                 
[  OK  ] Stopped Mosquitto - lightweight server implementatio...T-SN protocols. 
[  OK  ] Stopped Intel_XDK_Daemon.                                              
[  OK  ] Unmounted Mount for factory.                                           
         Stopping Zero-configuration networking...                              
[  OK  ] Removed slice system-getty.slice.                                      
         Stopping Permit User Sessions...                                       
         Stopping Daemon to handle arduino sketches...                          
[  OK  ] Stopped Daemon to handle arduino sketches.                             
[  OK  ] Stopped Zero-configuration networking.                                 
[  OK  ] Stopped Permit User Sessions.                                          
[  OK  ] Stopped target Remote File Systems.                                    
[  OK  ] Stopped target Network.                                                
[  OK  ] Stopped target Basic System.                                           
[  OK  ] Stopped target Slices.                                                 
[  OK  ] Removed slice User and Session Slice.                                  
[  OK  ] Stopped target Paths.                                                  
[  OK  ] Stopped target Timers.                                                 
[  OK  ] Stopped target Sockets.                                                
[  OK  ] Closed sshd.socket.                                                    
[  OK  ] Closed RPCbind Server Activation Socket.                               
[  OK  ] Closed D-Bus System Message Bus Socket.                                
[  OK  ] Stopped target System Initialization.                                  
         Starting Console System Reboot Logging...                              
         Stopping Load/Save RF Kill Switch Status of rfkill1...                 
         Stopping Network Time Synchronization...                               
         Stopping Update UTMP about System Boot/Shutdown...                     
         Stopping Load Kernel Modules...                                        
[  OK  ] Stopped Load Kernel Modules.                                           
         Stopping Apply Kernel Variables...                                     
[  OK  ] Stopped Apply Kernel Variables.                                        
         Stopping Load/Save Random Seed...                                      
[  OK  ] Stopped target Swap.                                                   
         Stopping Load/Save RF Kill Switch Status of rfkill0...                 
[  OK  ] Stopped Network Time Synchronization.                                  
[  OK  ] Started Console System Reboot Logging.                                 
[  OK  ] Stopped Load/Save RF Kill Switch Status of rfkill1.                    
[  OK  ] Stopped Update UTMP about System Boot/Shutdown.                        
[  OK  ] Stopped Load/Save Random Seed.                                         
[  OK  ] Stopped Load/Save RF Kill Switch Status of rfkill0.                    
[  OK  ] Removed slice system-systemd\x2drfkill.slice.                          
         Stopping Create Volatile Files and Directories...                      
[  OK  ] Stopped Create Volatile Files and Directories.                         
[  OK  ] Stopped target Local File Systems.                                     
         Unmounting /run/user/0...                                              
[  OK  ] Unset automount boot.automount.                                        
         Unmounting /var/volatile...                                            
         Unmounting Temporary Directory...                                      
[  OK  ] Unmounted /run/user/0.                                                 
[  OK  ] Failed unmounting /var/volatile.                                       
[  OK  ] Unmounted Temporary Directory.                                         
[  OK  ] Reached target Unmount All Filesystems.                                
[  OK  ] Stopped target Local File Systems (Pre).                               
         Stopping Remount Root and Kernel File Systems...                       
[  OK  ] Stopped Remount Root and Kernel File Systems.                          
[  OK  ] Reached target Shutdown.                                               

```