# reliable_data_transfer
simple TCP protocol implementation over unreliable channels  
compiled with x64 mode  
  
features:  
1, cumulative ACKs with pipelining   
2, fast re-transmit  
3, flow control  
4, single timer for the base of the window  
5, exponential timer backoff during loss  

More details and performance see report pdf  
  
  
Usage:  
reliable_data_transfer.exe hostname/IP \  
         power-of-2 buffer size to be transmitted (in DWORDs) \  
         sender window (in packets) \  
         round-trip propagation delay (in seconds) \  
         probability of loss in forward direction \  
         probability of loss in return direction \  
         speed of the bottleneck link (in Mbps)  
Example : reliable_data_transfer.exe s8.irl.cs.tamu.edu 24 50000 0.2 0.00001 0.0001 100  
  
  
Example traces:  
Packet size 1500 bytes:   
Main:   sender W = 8192, RTT 0.100 sec, loss 0 / 0, link 1000 Mbps   
Main:   initializing DWORD array with 2^29 elements... done in 1936 ms   
Main:   connected to 127.0.0.1 in 0.002 sec, pkt size 1472 bytes  
[ 2] B  47895 (67.6 MB) N       47899 T 0 F 0 W 8192 S 280.497 Mbps RTT 0.000  
[ 4] B  101990 (144.0 MB) N     102001 T 0 F 0 W 8192 S 316.587 Mbps RTT 0.000  
[ 6] B  147989 (208.9 MB) N     147992 T 0 F 0 W 8192 S 268.960 Mbps RTT 0.000  
[ 8] B  202060 (285.2 MB) N     202063 T 0 F 0 W 8192 S 316.435 Mbps RTT 0.000  
[ 10] B 263773 (372.3 MB) N     263778 T 0 F 0 W 8192 S 361.210 Mbps RTT 0.000  
[ 12] B 305854 (431.7 MB) N     305855 T 0 F 0 W 8192 S 246.204 Mbps RTT 0.000  
[ 14] B 349315 (493.0 MB) N     349316 T 0 F 0 W 8192 S 254.309 Mbps RTT 0.000  
[ 16] B 413828 (584.1 MB) N     414712 T 0 F 0 W 8192 S 382.736 Mbps RTT 0.012  
[ 18] B 487360 (687.9 MB) N     487361 T 0 F 0 W 8192 S 424.952 Mbps RTT 0.001  
[ 20] B 532133 (751.1 MB) N     532135 T 0 F 0 W 8192 S 261.939 Mbps RTT 0.001  
[ 22] B 592226 (835.9 MB) N     592236 T 0 F 0 W 8192 S 351.735 Mbps RTT 0.001  
[ 24] B 662758 (935.4 MB) N     662769 T 0 F 0 W 8192 S 412.737 Mbps RTT 0.001  
[ 26] B 722031 (1019.1 MB) N    722035 T 0 F 0 W 8192 S 346.722 Mbps RTT 0.000  
[ 28] B 767237 (1082.9 MB) N    767239 T 0 F 0 W 8192 S 264.445 Mbps RTT 0.000  
[ 30] B 814684 (1149.9 MB) N    814688 T 0 F 0 W 8192 S 277.615 Mbps RTT 0.000  
[ 32] B 864743 (1220.5 MB) N    864745 T 0 F 0 W 8192 S 292.753 Mbps RTT 0.000  
[ 34] B 913022 (1288.7 MB) N    913026 T 0 F 0 W 8192 S 282.687 Mbps RTT 0.000  
[ 36] B 964776 (1361.7 MB) N    964780 T 0 F 0 W 8192 S 303.001 Mbps RTT 0.000  
[ 38] B 1022123 (1442.7 MB) N   1022127 T 0 F 0 W 8192 S 335.783 Mbps RTT 0.000  
[ 40] B 1069238 (1509.2 MB) N   1069239 T 0 F 0 W 8192 S 275.847 Mbps RTT 0.000  
[ 42] B 1110958 (1568.0 MB) N   1110959 T 0 F 0 W 8192 S 244.277 Mbps RTT 0.001  
[ 44] B 1164838 (1644.1 MB) N   1164842 T 0 F 0 W 8192 S 315.498 Mbps RTT 0.000  
[ 46] B 1214344 (1714.0 MB) N   1214348 T 0 F 0 W 8192 S 289.849 Mbps RTT 0.000  
[ 48] B 1269329 (1791.6 MB) N   1269330 T 0 F 0 W 8192 S 321.939 Mbps RTT 0.000   
[ 50] B 1311699 (1851.4 MB) N   1311700 T 0 F 0 W 8192 S 248.078 Mbps RTT 0.000   
[ 52] B 1371679 (1936.0 MB) N   1371797 T 0 F 0 W 8192 S 351.893 Mbps RTT 0.001   
[ 54] B 1453938 (2052.1 MB) N   1453945 T 0 F 0 W 8192 S 480.965 Mbps RTT 0.000   
[ 54.302] <-- FIN-ACK 1466861 window 0   
Main:   transfer finished in 54.285 sec, 316475.47 Kbps, checksum: ef5f9797   
Main:   estRTT 0.000, ideal rate inf Kbps   
