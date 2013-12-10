#BlackBerry 10 IPSec VPN Setup

>Now that you have your StrongSwan IPSec VPN setup now you want to connect to it

##Import your cert

>plug in your blackberry10 device into your computer and transfer you CA.cer to you phone. remember where you put it on your device so you can import it

**Settings->Security and Privacy->Certificates**

>press the **+ import** button on the bottom. Now find the CA.cer cert on your phone.
>It will say **About to import certificate StrongSwan CA**
>Check **Restrict usage to VPN**
>Then press next and it will import your cert$

##Configure VPN 

**Settings->Network and Connections->VPN**

>press the **+ Add** button on the bottom

>**Profile Name:** *what you want*

>**Server Address:** *your domain or ip address*

>**Gateway Type:** *Microsoft IKEv2 VPN Server*

>**Authentication Type:** *EAP-MSCHAPv2*

>**Authentication ID Type:** *Fully Qualified Domain Name*

>**Authentication ID:** *your login*

>**MSCHAPv2 Password:** *your password*

>**Gateway Auth Type:** *PKI*

>**Gateway Auth ID Type:** *Identity Certificate Distinguished Name*

>**Gateway CA Certificate:** *StrongSwan CA*

>Now press **Save** button on the bottom

##Using the VPN on your BlackBerry 10 device

>Now that your have you VPN configured you can connect to your VPN at any time you want by going to Settings->Network and Connections->VPN and pressing on the VPN profile you created. 

>You can also setup wifi profiles that use this VPN profile so you can have added security when connecting to open or less secure hotsopts

**Contact me**

[Email](mailto:badtoyz@gmail.com) - [Twitter](https://twitter.com/badtoyz) - [Github](https://github.com/badtoyz)
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.