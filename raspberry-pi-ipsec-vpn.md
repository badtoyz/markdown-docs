#Raspberry Pi IPSec VPN

This is the setup for a ipsec vpn running on a raspberry pi. I have set one up and running so i can access my home network from anyware i am with my BlackBerry Z10

##Requrerments 

*   [Raspberry Pi](http://www.raspberrypi.org/)
*   [Raspian](http://www.raspbian.org/)
*   [StrongSwan for raspberry pi](http://www.strongswan.org/)


##Install strongswan

     echo "deb http://p.quinput.eu/debfarm/ unstable all" >> /etc/apt/sources.list
     apt-get update
     apt-get install strongswan

##Add configuration

*Copy the following into /etc/strongswan.conf*
    charon {
        plugins {                
            dhcp {
        identity_lease = yes
        }
        }
    }

    libstrongswan {
    }

*Copy the following into /etc/ipsec.conf*
    
    config setup
    conn %default
        auto=add
        left=%any
        leftsubnet=0.0.0.0/0
        right=%any
        rightsourceip=%dhcp
        forceencaps=yes
        compress=yes
    conn rw-eap
        dpdaction=clear
        dpddelay=300s
        leftauth=pubkey
        leftcert=serverCert.pem
        rightauth=eap-mschapv2
        rightsendcert=never

*Copy the following into /etc/ipsec.secrets. Here 2 users/pass are declared*
    
    alice : XAUTH "wonderland"
    bob : XAUTH "builder"
    : RSA serverKey.pem

>These are just test user names and password. change then to what you need

*Copy the following into /etc/sysctl.conf*

    net.ipv4.ip_forward = 1
    net.ipv4.conf.default.proxy_arp = 1
    net.ipv4.conf.default.arp_accept = 1
    net.ipv4.conf.default.proxy_arp_pvlan = 1

##Generate certs

*Run these commands. Replace H with your FQDN (some clients will check that it matches)*

>Replace your.domain.com with your ip or domain name. you can use a serves like dyndns

    export H=your.domain.com

    ipsec pki --gen --outform pem > caKey.pem
    ipsec pki --self --in caKey.pem --dn "C=FR, O=strongSwan, CN=strongSwan CA" --ca --outform pem > caCert.pem
    ipsec pki --gen --outform pem > serverKey.pem
    ipsec pki --pub --in serverKey.pem | ipsec pki --issue --cacert caCert.pem --cakey caKey.pem \
              --dn "C=FR, O=strongSwan, CN=$H" --san="$H" \
              --flag serverAuth --flag ikeIntermediate --outform pem > serverCert.pem
    openssl x509 -inform PEM -outform DER -in caCert.pem -out CA.crt
    mv caCert.pem /etc/ipsec.d/cacerts/
    mv serverCert.pem /etc/ipsec.d/certs/
    mv serverKey.pem /etc/ipsec.d/private/

>For blackberry certs rename the CA.crt to CA.cer 

##Adding IPSec to run at boot
    
    update-rc.d ipsec defaults

##Firewall

Open up ports udp 500 and udp 4500 to let them through to the vpn server. Here you will have to do port forwarding with your router

