# Corch-Crackme - competition crackme v1.0 by corch#2222

 >[Download from Crackmes.one](https://crackmes.one/crackme/62b6efd133c5d4251e7239c2)

After unzipping rar we get one .exe file named "Crackme.exe". when we run that file it asks us a password. 
in crackmess one description author state that we can patch it or find password. 

first we can check it with pe scanning tool to get a idea , i'm using Detect It Easy 

![Screenshot 2022-10-14 121116.png](attachment:51cf5557-88fa-406f-8e03-25dda53f8d0f.png)

![Screenshot 2022-10-14 121345.png](attachment:1304cc0c-e6e6-46bf-a500-b1f0883ff891.png)

Looks like it is not packed. 

## Load it up with a debugger


without any anti-anti-debug plugins enabled , it show a message in console "You have been detected !". lets find out how they detect the debugger


- looking at import address table we can see there are some Win32 API's that can detect a debugger. by searching all intermodular calls in exe , we can see where these apis get called. 
    - IsDebuggerPresent
    - FindWindowA
    
![isdebuggerpresent1.png](attachment:61b2045e-3a88-4db7-904f-667205de4e94.png)
![findwindowa.png](attachment:0de2a956-f88c-4725-970c-06fbd2b187c4.png)

we can simply use ScyllaHide pluging to bypass these anti-debug tricks. 

![scyllahideoptions.png](attachment:434fa850-21cc-4be2-9082-bc0d8373620d.png)


