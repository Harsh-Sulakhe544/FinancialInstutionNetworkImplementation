what is broadcast address : 
subnet mask =  255.255.255.255 – Represents the broadcast address, or place to route messages to be sent to every device within a network

A = Network class A ip here , actually any ip network 
A /27 subnet mask means that 27 of the 32 bits of the address are the netmask. This means that only 5 bits are available to differentiate the 
computers  ==>  However, you always lose 2 addresses for broadcast and loopback, so the result is: 2^(32–27) — 2 = 2⁵ -2 = 32–2 =30. We have 
only 30 usable addresses on /27 allocations. , 
255-30 => 224  (dont include loopback and broadcast)

wherever we give '>' => that is command 
Financia Institutionl Network System  Design and Implementation

A = Network Design and Beautification 
SEQUENCE TO PLAY DEVICES  
1. 4 routers 2911,
2. Use 2 Mutilayer Switches 3650-24PS
3. for all 4 routers , turn off the switch and place HWIC-2T module in router , and again turn on Router
4. 1 2811 router for VoIp , telephone service
5. place devices like 
3pc's  2 ip phones , 1 Printer, 1 lptop, 1 access point (normal) => wireless,  1 smartphone and 1 tablet-pc =>we can see that access point is 
directly connected wirelessly to smart-phone and tablet-pc
we see that smartphone and Tablet gets automatically connected to Access point 
6. copy paste 5th point devices for all 4 extra switches 
7. place 4 servers => Server pt => connect it to the Switch-5 

questions : 
if we dont understand cabling , then we just use => automatically connection type cable(red symbol)

why AC Power Supply to Switches => AC switches are capable of interrupting the current flow during both 
positive and negative half-cycles, making them suitable for controlling AC power sources. 

why voip protocol for phones 
VoIP (Voice over Internet Protocol) phones allow voice calls to be transmitted digitally over the internet instead of traditional phone lines. 

why adapters => to power the voip-phone : 
An adapter or adaptor is a device that converts attributes of one electrical device or system to those of an otherwise incompatible device or 
system.

why access point 
In an all-wireless network, an access point acts as a standalone root uni
It serves as the focal point for communications, increasing the communication range of wireless users.

ERRORS : 
switches : why orange color => sometimes port is diabled or due to heavy traffic (not proper topology of conection)
            green - success no connection => traffic is managed 
MODULES TO INSTALL IN DEVICES 
1. AC power Supply module in first of => MultiLayer Switch to both
2. from the laptop , switch of and remove the module and add wpc-300n into the laptop => and again switch on  => laptop gets auto connected to 
access point
CHANGING THE PORT NAME , MAKES THE SERVICE INACTIVE FOR MOST OF ROUTER DEVICES 
3. go to access point , and config and port1 => change the port status => Default2 (or any name)  ==> access point gets disconnected to the 
wireless devices(smartphone, tablet-pc, laptop )
4. click voip-phone => put ip_phone_power_adapter to the exact-below-rs-232 part  => make this to both the phones => voip gets configured 

B = basic settings to all devices + ssh on the routers and 13 switches 
commands 
switches : 
switch > en  => to enabel / turn on 
... > conf t => configure the terminal   
... > hostname HR-SW => to set the hostname to be HR-SW
... > enable password cisco => cisco is username of this Device => each time u want to change something with the HR-Switch

console settings 
... > line console 0 => { to enable the console , When you enter "line con 0", you enter a configuration mode that is specific to the console. 
        Any commands entered there will not apply. }
... > password cisco => console password is cisco , for username above who is cisco
... > login => to tell to authenticate on the login each time 
... > exit => to exit the ssh-configuration mode  or any mode 

to give a banner message , upon failure of password to access the devices
Switch > banner motd #No UNAUTHORISED ACCESS!!!!#

no ip domain lookup => for switches 
Switch > service password-encryption => for password encrypion 
Switch > do wr  ==> do write => to build dependencies/configurations for any of the devices => here switches 

commands , do above commands for all layer3 switches, routers (do not use router 2811 => voip )(but hostname = HR_SW, CS-SW,Sever-Side, 
(multilayer SW) => MLSW ...)

if u did not follow the order for configuring , just start once again fom mistake has happen 
for ex: if u missed command => no ip lookup domain => start from that command or it's previous(banner ...) 

note : { while building dependencies for multilayer-switches => it will compress configurations }   

adding ssh/configuring ssh  =>  hostname => do this same for CS-MLSW,(Routers except 2811)... and all switches uptill now
if it asks for pasword anywhere => "cisco" in between ssh keys 
1.configure hostname => HQ-MLSW  => en , conf t => to get to configuration mode 
2. HQ-MLSW > username cisco password cisco => actualusername and user-password
3. ip domain-name cisco.com => to set the domain(web-address) to the default cisco.com
4 to generate ssh key => 
crypto key generate rsa => rsa: Algorithm 
5. 1024 bits => number of bits of ssh  keys 
6. ip ssh version 2 => 2nd version of ssh 
vty => virtual teletype 
7. line vty 0 15 => Lines 0 15 is vty lines 0, 1, 2 ,3 ,4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14 and 15. for 
        example if you were type in global configuration mode, line vty 0 15 you will enter configuration for 
        lines 0-15. 

        The command line vty 0 15 is used to configure Virtual Terminal (VTY) lines 0–15 on a Cisco device. 
        VTY lines are virtual lines that allow users to remotely access a device using Secure Shell (SSH) or 
        Telnet.

        OR  
        The command line vty 0 4 means that the device can allow 5 simultaneous virtual connections which may be Telnet or SSH.

        VTY lines are logical interfaces of a device and are often used in network devices like routers and 
        switches. Administrators can use VTY lines to configure, manage, and monitor a device remotely.

8. login local => In SSH, "login local" means that the router should use the local database 
        for authentication. (here local database cisco's - user's database)
        "Login local" asks the person logging in to enter a username and password that are stored on the 
        router. You can add an account to the local database using the "username" command.

9 transport input ssh => The command "transport input ssh" is used by Cisco to set which protocols 
        are allowed to access the virtual terminal lines. , u can also do 
        The command "transport input ssh telnet" means only these two protocols will have access to the VTY 
        lines.

10 exit 
11 do wr => to build dependencies/configurations => rules   

TO MAKE VLANS :  
config vlans(data and voice ) + all access on trunk ports on l2 and l3 switches (l=layer)     
ex : vlan => HR Department =>2-vlans=> (data = 10 , voiceID = 120) (u can take anything ) , paste this to all other the departments (CS, LM,ID,
MK) 
for ever port on each switch 
to create vlan => switch -> config-> for fast-ethernet4 => (password: cisco)

HR-SW > en
... > conf t
... > exit => to exit the configuration if 
... > vlan 10 =>
VLAN 10 and VLAN 20 are different IP sub-networks.VLAN stands for Virtual Local Area Network For example, you can assign VLAN 10 to sales and 
VLAN 20 to marketing. If a sales PC sends out a broadcast packet, it will also reach another sales PC or PCs assigned with VLAN 10.

{ what is that 10 exactly => unique vlan id  or 
VLANs are broadcast domains identified by a VLAN ID, which is a number between 0 and 4095. The default VLAN on any network is VLAN 1 }

... > name DATA => name of the vlan 10 

... > vlan 120
> name  VOICE => name of the vlan 120

Since check HR-SW => the fa0 and fa1 are connected to 2 MLSW above , so trunk them , commands 
HR-SW(config-vlan)  > int range fa0/1-2 => select 1-2 ports are interface   , 

now trunk these 2 ports  => What Does Trunk Port Mean? 
A trunk port is a specific type of port on a network switch that allows data to flow 
across a network node for multiple virtual local area networks or VLANs. Think of the trunk port as a “bundle” of individual branches or 
capillaries in a telecom network connection.

HR-SW(config-vlan-if-range) > switchport mode trunk
enter 
exit

Now we want remaining ports to Access mode  => 3-24 
HR-SW(config) > int range fa0/3-24
HR-SW(config-if-range) > switchport mode access  ==> 
The command switchport mode access configures a Cisco IOS device's Layer 2 interface to operate in access mode. This command forces the port 
to be an access port, which means that only devices in the same VLAN can communicate with it.

difference between trunk Modes vs Access Modes => https://ipwithease.com/switchport-trunk-mode-vs-access-mode/
trunk => static , access => dynamic 

how to add actual-data to vlan's (ex  vlan id is 10  )

HR-SW(config-if-range) > switchport access vlan 10 => for DATA vlan , 10 is id

HR-SW(config-if-range) > switchport voice vlan 120 => for VOICE vlan , 120 is id 

exit
do wr => build the dependencies/configurations
do sh start => do show start => u press enter and check fa0/1-24 => whether they are trunked or access 
==> show's spanning tree ==> press enter enter to view more ethernet's

==> after doing this Switch is configure with router and all other devices  (do this for all other departments => CS, LM,ID,MK ) , but change 
VLAN to 20,30,40,50 , Remember that 120 is constant because of VOICE 

no vlan 10 => to delete a particular vlan with id 10 => repeat all the previous commands 

now configure the layer3 = "multilayer-switches" => do not consider upper routers of ML-SW , but consider voip router 2811 , 
cuz we pass voice of SW-MLSW => then to router 2811, 
router 2811 => "default gateway" for all switches 

FOR L3 SWITCHES , DO THSIS FOR CS-MLSW 
trunk for multilayer - switches => config-> GigaBitEthernet1/0/5  => cli , then 
HQ-MLSW > en , conf t , 
... > int range gig1/0/2-7 
... config-if-range > switchport mode trunk
... => exit

now Create the vlan's for all the departments and configure the trunk interface 
> vlan 10 
>name HR
> vlan 20 
>name CS
> vlan 30 
>name MK
> vlan 40 
>name LM
> vlan 50 
>name IT
>vlan 120 
> name VOICE

>exit
> do wr 

do this above same for CS-MLSW but 2-6 , INSTEAD OF  => int range gig1/0/2-7 , CUZ NOP ROUTER 2811 CONNECTED DIRECTLY (BUT INDIRECTLY VIA 
HQ-MLSW)

3. switchport security to server-side-department  (fa0/2-5  ==> 2 to 5 ports ), don't consider routers , only external servers => web,dhcp...
click-Server-Side-SW => config->fa0/2 =>cli 
config-if > exit => to exit config-if 
config > int range fa0/2-5
config > switchport mode access 

to make port security 
config-if-range > switchport port-security  maximum 1 => complete secured , but only 1 device connect to port at one time 
config-if-range > switchport port-security  mac-address sticky => static mac-address , no time limit  

config-if-range > switchport port-security  violation shutdown => The default violation mode is shutdown. When a violation occurs in shutdown 
mode, the switchport will be taken out of service and put in an error-disabled state. The switchport will remain in this state until manually 
removed.  

how to recover , when we restart the computer ? => 
To get the interface out of the err-disable state, you need to type “shutdown” followed by “no shutdown”.

... > exit
> do wr
> do sh start  ==> press enter-enter-enter - till last we exit that spanning tree 

but if someone makes other ports of same switch to conect to other devices, other than web, dhcp, ...  --- security broken ??? 
MALICIOUS DHCP SERVER  (2-5 connected to server ) => we need to make the remaining secure 

config > int range fa0/6-24, gig0/1-2 => also seure both fa and gig ports 
config-if-range > switchport mode access 
config-if-range > switchport  access vlan 99 => not exists creates vlan 99 => "testing fake "
config-if-range > shutdown 
> exit
> do wr
> do sh start 
press enter - enter =>( shutdown state  ==> check port 6 - 24  )

to check all the final port security 
> do sh port-security  => 2 to 5 secured , and all other details  => sometimes this command may or may not work 

4 SUBNETTING AND IP ADDRESSING , (dividing the ip 255 => 11111111 => 8 bits are set to 1 , 0 => 00000000 => 8 bits are not set )
GIVEN IN DATA => 192.168.20.0/24 ,  (THAT 24  MEANS => 24 BITS ARE SET FOR USED FOR NEWTORK , REMAINING 8 
BITS ARE HOST ADDRESS  SUBNET MASK => 255.255.255.0 , AT LAST .0 -- .255 => WE CAN ASSIGN 255 UNIQUE DEVICES/hosts ) ,

VOICE => 10.10.10.0/24 , PUBLIC-IP => 10.200.100.0 => given 

check the images => server-ip and destination-ip  in path  => C:\Users\itzha\Pictures\Screenshots
START ASSIGNING IP-Addressing with routers 2811 
click router => fa0/0 => cli => 
commands : 
        {{ no sh => turn the router on 
        (en , conf t => enable and configure the terminal ) => u can skip this also , make sure u are in config-if
        router-config-if >  ip add 10.10.10.0  255.255.255.0 => subnet mask is 255.255.255.0 , ip-address is 10.10.10.0
        > exit } }    
        ==> WRONG , I WANT VLAN VOICE (SUB-NET TO HAVE THIS IP )

TO DELETE the above ip-adress and settings 
> GOTO FA0/0 => cli => 
router-config-if>  no ip add     ===> delete the ip address,sub-net mask 

 i need to shift to vlan 120 => voice vlan 
router-config-if > int FastEthernet0/0.120  => 120 is the id of VOICE VLAN
router-config-subif > encapsulation dot1q 120  ==> used to configure Q-in-Q termination on a subinterface. It is configurable on Ethernet 
and EtherChannel interfaces

why 1Q => IEEE 802.1Q is a standard protocol for connecting multiple switches and routers, and for defining VLAN topologies. The encapsulation 
dot1Q command tells the switch that the interface should use IEEE 802.1Q encapsulation on the frames when the interface is configured as a 
trunk 

router-config-subif > ip add 10.10.10.0  255.255.255.0
router-config-subif  > exit 
> do wr ==> building configurations (rules for the voip routers)

now for the MLSW - let's subnet  => make MLSW => to layer3 interface  => HQ-MLSW && CS-MLSW (both everything is same , make CS-MLSW => ip as 
192.168.21.21)
HQ-MLSW => gig1/0/1
HQ-MLSW-config-if > no switchport  => it is not a port for the swith anymore now , indepenedent to behave, 
netowrk is 192.168.21.16 => we make the host to be  17  (we can take any number other than 16 )
HQ-MLSW-config-if > ip add 192.168.21.17  255.255.255.252  
... > no shut => no shutdown 
... > do wr 

HQ-Router : 
same above procedure for Router also , we can do it manually , same router gigabitEthernet0/0 , gi0/1, se0/2/0 and se0/2/1 ==> configure all 4 
(all gig and serial ports )
HQ-router-click => config => gigabitEthernet0/0 => in the RHS Side =>   ipv4 - 192.168.21.18 , subnet mask = 255.255.255.252 (add both then 
close , otherwise error ) , same router gi0/1, se0/2/0 and se0/2/1 ==> configure all 4 
gig0/1 => ipv4 = 192.168.21.22  subnet mask = 255.255.255.252
se0/2/0 => 190.200.100.1 and 255.255.255.252
se0/2/1 => 190.200.100.5 and 255.255.255.252  
HQ-Router > no sh,  do wr => do not shutdown and  build the configurations => otherwise everything goes in vain 

Safaricom-isp  Router : 
se0/2/0 => ipv4 190.200.100.2 subnet 255.255.255.252
se0/2/1 => ipv4 190.200.100.10 subnet 255.255.255.252

Safaricom-isp  Router > no sh , do wr 

JTL-isp  Router : 
se0/2/0 => ipv4 190.200.100.6 subnet 255.255.255.252
se0/2/1 => ipv4 190.200.100.14 subnet 255.255.255.252

JTL-isp  Router > no sh , do wr 

Server side Router 
Server Side Router > 
se0/2/0 => ipv4 190.200.100.9 subnet 255.255.255.252
se0/2/1 => ipv4 190.200.100.13 subnet 255.255.255.252
gig0/0 => ipv4 = 192.168.21.1 subnet mask = 255.255.255.240
... > no sh , do wr 

if no sh is not working , ==> router => config => fa0/0 (any port ) => top rioght side in gui => port status => on check that box  , 
cli >> do wr => do remember to build the dependencies 

5 OSPF(Routing Algorithm) on the routers and layer3 switches 
goto the MLSW's => enable the ip routing on both HQ-MLSW and CS-MLSW
MLSW > en , conf t => to enable and configure the setings , 
( password ? ) {password : cisco }
HQ-MLSW-config > ip routing 
CS-MLSW-config > ip routing 

then we want to apply OSPF Algorithm  default distance is 100 (for immediate next node ) 
HQ-MLSW-config > router ospf 10  ==> 10 is the distance from MLSW to any of the (next immediate device/switch/router) 
if we have A-B-C => 3 nodes ,  
on A if we apply OSPF => A-B => 10 is distance  , A-c => distance may change depend on B-C

HQ-MLSW-config-router => router-id 1.1.1.1 

THIS ROUTER HAS 3 NETWORKS CONNECTED => VOICE ,DATA,  HQ-ROUTER => 3  
-------VOICE 
HQ-MLSW-config-router >  network 10.10.10.0   0.0.0.255  area 0  , (ip, subnet, area ) ==> ( network, ip-address, wildcard-mask, area 
area-id  ) => at last 255 - 0 = 255 

why area  0 ?  ==> within same area so 0 

-------DATA
HQ-MLSW-config-router >  network 192.168.21.16   0.0.0.3  area 0 
==> wildcard => left over device to connect wrt subnet-mask => 255.255.255.252 => we see 255 should be at last , so 255-252 = 3 networks

-------HQ-ROUTER
HQ-MLSW-config-router >  network 192.168.20.0   0.0.0.255  area 0 

... > exit 
... > do wr 

do this same for CS-MLSW => but 
CS-MLSW-config-router> router-id 2.2.2.2

remember n = number of networks for particular MLSW
CS-MLSW > en , conf t , ip routing, router ospf 10 router-id 2.2.2.2 , network  ipv4  wild-card-mask  area 0 * n ==> 
network 10.10.10.0   0.0.0.255  area 0 => VOICE
network 192.168.21.20   0.0.0.3  area 0 => DATA
network 192.168.20.0   0.0.0.255  area 0 => HQ-ROUTER

> exit 
> do wr 

next is:  HQ-VOIP-Router 2811   .make sure the port is on FastEthernet0/0 in gui in config 
> en , conf t , int FastEthernet0/0 , exit 
config > router ospf 10 
config-router> router-id 3.3.3.3
config-router > network 192.168.20.0   0.0.0.255  area 0 => HQ-ROUTER
... > exit 
... > do wr 

same for HQ-ROUTER  =>here we have 4 networks 
router ospf 10 
router-config > router-id 4.4.4.4 
... > network 192.168.21.20   0.0.0.3  area 0 
confirmation ==>  GigabitEthernet0/1 from LOADING to FULL, Loading Done
> network 190.200.100.0   0.0.0.3  area 0 
> network 190.200.100.4   0.0.0.3  area 0 
> exit 
> do wr 

OSPF => ADJACENT ROUTER SHOULD RESPOND => SHORTEST PATH 

Now Safricorn-ISP router  ==> config => Serial0/2/0 => cli 
> exit 
> router ospf 10 
> router-id 5.5.5.5
> network 190.200.100.0   0.0.0.3  area 0   
==> confirmation  => 02:09:28: %OSPF-5-ADJCHG: Process 10, Nbr 4.4.4.4 on Serial0/2/0 from LOADING to FULL, Loading Done
> network 190.200.100.8   0.0.0.3  area 0 
> exit 
> do wr 

Now JTL-ISP router  ==> config => gig0/0 => cli 
> exit 
> router ospf 10 
> router-id 6.6.6.6
> network 190.200.100.4   0.0.0.3  area 0   
==> confirmation  => 02:09:28: %OSPF-5-ADJCHG: Process 10, Nbr 4.4.4.4 on Serial0/2/0 from LOADING to FULL, Loading Done
> network 190.200.100.12   0.0.0.3  area 0 
> exit 
> do wr 

Now Server-Side router  ==> config => gig0/2 => cli  , 255-240 => 15 devices can connect 
> exit 
> router ospf 10 
> router-id 7.7.7.7
> network 192.168.21.0   0.0.0.15  area 0   
==> confirmation  => 02:09:28: %OSPF-5-ADJCHG: Process 10, Nbr 4.4.4.4 on Serial0/2/0 from LOADING to FULL, Loading Done
> network 190.200.100.12   0.0.0.3  area 0 
> network 190.200.100.8   0.0.0.3  area 0 
> exit 
> do wr 

TO CHECK THE OSPF ADJACENCY PATHS , go to any of the router  
config-router > do sh ip ospf neigh   ==> neighbour 

6. Static IP Address to ServerRoom Devices 
for DHCP server =>
click on it =>  Desktop => ip-configuration  => ipv4 => 192.168.21.5  , subnet-mask = 255.255.255.240   , cuz of  .NET/28 
Default-gaTEWAY => 192.168.21.1 , DNS- 192.168.21.6  => STATIC Configuration 

for DNS server =>
click on it =>  Desktop => ip-configuration  => ipv4 => 192.168.21.6  , subnet-mask = 255.255.255.240   , cuz of  .NET/28 
Default-gaTEWAY => 192.168.21.1 , DNS- 192.168.21.6  => STATIC Configuration 

for WEB server =>
click on it =>  Desktop => ip-configuration  => ipv4 => 192.168.21.7  , subnet-mask = 255.255.255.240   , cuz of  .NET/28 
Default-gaTEWAY => 192.168.21.1 , DNS- 192.168.21.6  => STATIC Configuration 

for email server =>
click on it =>  Desktop => ip-configuration  => ipv4 => 192.168.21.8  , subnet-mask = 255.255.255.240   , cuz of  .NET/28 
Default-gaTEWAY => 192.168.21.1 , DNS- 192.168.21.6  => STATIC Configuration 

7. DHCP SERVER DEVICE CONFIGURATION 

NOW CREATE A POOLS : what is a POOL ? why pool 
Network Pool. When the device is serving as a DHCP server, one or more pools of IP addresses must be defined, from which the device will 
allocate IP addresses to DHCP clients. Each network pool contains a range of addresses that belong to a specific subnet

Network system pools simplify and automate network configuration tasks for virtual servers.

DHCP-SERVER = click on it => services => DHCP => PORTNAME => serverPool
service-on  and Start-ip - 0.0.0.0 in 4 seperate columns  , subnet-mask is  255.255.255.0
max-no-of-users = 0  => SAVE

NOW ADD DIFF POOLS ON SAME DHCP SERVER (it)
click on it => services => DHCP => portname : HRPool
defaultgateway => 192.168.20.1 ,  => .NET ADDRESS is .0 => (so use .0 -- anything for this network devices)
DNS Server => 192.168.21.6 
start-ip-address => 192.168.20.5
subnet-mask 255.255.255.192
max-no-of-users = 60  => SAVE

NOW CSPool 
click on it => services => DHCP => portname : CSPool 
defaultgateway => 192.168.20.65 , => .NET ADDRESS is .64 (so use . 64 -- anything for this network devices)
DNS Server => 192.168.21.6 
start-ip-address => 192.168.20.70
subnet-mask 255.255.255.192
max-no-of-users = 59  => ADD

NOW MKPool 
click on it => services => DHCP => portname :MKPool 
defaultgateway => 192.168.20.129 , => .NET ADDRESS is .128 (so use . 128 -- anything for this network devices)
DNS Server => 192.168.21.6 
start-ip-address => 192.168.20.135
subnet-mask 255.255.255.192
max-no-of-users = 58  => ADD

NOW LMPool 
click on it => services => DHCP => portname : LMPool 
defaultgateway => 192.168.20.193 , => .NET ADDRESS is .192 , ( so use .193 -- anything for this network devices)
DNS Server => 192.168.21.6 
start-ip-address => 192.168.20.196
subnet-mask 255.255.255.224
max-no-of-users = 28  => ADD

NOW ITPool 
click on it => services => DHCP => portname :ITPool 
defaultgateway => 192.168.20.225 , => .NET ADDRESS is .224 , ( so use .224 -- anything for this network devices)
DNS Server => 192.168.21.6 
start-ip-address => 192.168.20.230
subnet-mask 255.255.255.224
max-no-of-users = 28  => ADD

do not save => just close 

8. INTER-VLAN ROUTING ON L3 SWITCHES + DHCP HELPER ADDRESS ==> " basically forward your(HR's pc, PRINTER , also from 
other departments CS, MK, LM, IT through .NET ) request to this DHCP-SERVER " via MLSW-Router-Router-Switch-DHCP-Server

we need to configure both the MLSW to reach 5 vlan's (HR, CS , ...) + ( DHCP-Server ip address to reach to both the MLSW )

we need to create a sub interface for VLAN 10, 20 , 30 , 40 , 50  and assign them ip addresses and their subnets respectively
goto HQ-MLSW => click => config => gigFa/04 =>  cli => 
config-if > exit
config => (to check vlan => "do sh vlan" => do show vlan) 

HR-department - vlan 10 => ip address for vlan 10 interface should correspond  with default gateway of  vlan 10 , 
(similar with other vlan 20,30...)

MLSW-HQ config > int vlan 10   => to reach vlan 10
MLSW-HQ config-if > ip add 192.168.20.1 255.255.255.192  

do not forget dhcp-hepler addresss => grab dhcp-server ip from Server side
basically forward your request to this DHCP-SERVER 

MLSW-HQ config-if > ip helper-address 192.168.21.5  ==> DHCP-Server-ip-address 
MLSW-HQ config > exit 

vlan 20
MLSW-HQ config > int vlan 20   => to reach vlan 20
MLSW-HQ config-if > ip add 192.168.20.65 255.255.255.192  

MLSW-HQ config-if > ip helper-address 192.168.21.5  
MLSW-HQ config > exit 

vlan 30
MLSW-HQ config > int vlan 30   => to reach vlan 30
MLSW-HQ config-if > ip add 192.168.20.129  255.255.255.192  
 
MLSW-HQ config-if > ip helper-address 192.168.21.5  
MLSW-HQ config > exit 

vlan 40
MLSW-HQ config > int vlan 40   => to reach vlan 40
MLSW-HQ config-if > ip add 192.168.20.193  255.255.255.224

MLSW-HQ config-if > ip helper-address 192.168.21.5  
MLSW-HQ config > exit 

vlan 50
MLSW-HQ config > int vlan 50   => to reach vlan 50
MLSW-HQ config-if > ip add 192.168.20.225  255.255.255.224   

MLSW-HQ config-if > ip helper-address 192.168.21.5  
MLSW-HQ config > exit 

... > do wr => to build the dependencies 

"DO the same to the CS-MLSW" for intervlan routing  => paste all the commands in cli for CS-MLSW

"TEST THE ABOVE BY MAKING HR-DEPARTMENT S ALL DEVICES Gateway/DNS IPV4  == DHCP (like HR-PC, HR-PRINTER) , THEN OTHER DEPARTMENTS , MAKE DHCP"
"FOR EXAMPLE , HR-DEPT PC's, PRINTER => they have picked IP-themselves , cuz of DHCP-Dynamic-Host protocol combo  "

IF ANY OF IP IS NOT PICKED , GOTO THAT DEPARTMENT , AND CLICK THAT DEVICE , MAKE IT'S GATEWAY-IPV4- DHCP ONCE AGAIN AND CHECK

8. WIRELESS NETWORKSs CONFIGURATIONS , 
 WHAT ABOUT SECURITY => { what is WPA-2-PSK ? 
==> WPA2-PSK stands for Wi-Fi Protected Access 2 – Pre-Shared Key. It is a security protocol used to secure wireless networks, particularly 
home and small office networks. WPA2-PSK was introduced as an upgrade to the original WPA standard, which proved to have vulnerabilities
 }
CLICK => HR-AP (access point) => config =>  port 1 => SSID(Server-Side-Identifier), Authenticiation(Security-password) => WPA-2-PSK => 
HR123456 (8 letters)  => remember this SSID, and password , 

then come to LAPTOP => config => wireless0 => SSID => "HR" , PASSWORD = "HR123456"  in WPA-2-PSK
then come to TABLET => config => wireless0 => SSID => "HR" , PASSWORD = "HR123456"  in WPA-2-PSK
then come to SMART-PHONE => config => wireless0 => SSID => "HR" , PASSWORD = "HR123456"  in WPA-2-PSK

CLICK => CS-AP (access point) => config =>  port 1 => SSID(Server-Side-Identifier), Authenticiation(Security-password) => WPA-2-PSK => 
CS123456 (8 letters)  => remember this SSID, and password , 

then come to LAPTOP => config => wireless0 => SSID => "HR" , PASSWORD = "CS123456"  in WPA-2-PSK
then come to TABLET => config => wireless0 => SSID => "HR" , PASSWORD = "CS123456"  in WPA-2-PSK
then come to SMART-PHONE => config => wireless0 => SSID => "HR" , PASSWORD = "CS123456"  in WPA-2-PSK

PERFORM THE SMAE FOR LM , MK , IT => PASSWORD AS "DEPT-NAME123456" IN AUTHENTICATION "WPA-2-PSK" 
==> ALL THESE DEVICES GET THE IP ADDRESS NOW BY ACCESS POINT  ==> Yes, wireless access points (WAPs) have IP addresses. A WAP is a network 
device that allows devices to connect to a wired network  
==> EX : LAPTOP => AP => HR-SWITCH => SEVERAL ROUTER'S  => DHCP'S SERVER => SO IP-V4 IS DONE 

10. configure HQ-VOIP Router  => TELEPHONY SERVICE CONFIGURATION
click on router => config => fa0/0  => cli 
... > exit
CREATE A POOL  

1ST ENABLE A DHCP SERVICE => for dynamic ip
config > service DHCP

now create a pool = voice 
config >  ip dhcp pool VOICE

2nd now create a network , here we have only 1 device voip-router ==> ip == .NET
dhcp-config >  network 10.10.10.0  255.255.255.0 
dhcp-config > default-router  10.10.10.1   

why default router ? , why 10.10.10.1 ? 
Usually, a default route is used in the following situations. To forward all packets to a single destination. To forward all unknown packets 
(whose destination network addresses are not available in the routing table) to a server or a device for logging and troubleshooting purposes.

10.10.10.1 is a private IP address that's used in internal network environments. It's often used as a gateway IP address on a private network

what is option 150 ? => TFTP for voip , 
DHCP option 150 is a Cisco option that tells clients the IP address of their TFTP server. Cisco IP phones download their configuration from a 
TFTP server. When a Cisco IP phone starts up and doesn't have the IP address and TFTP server IP address pre-configured, it sends a request 
with option 150 to the DHCP server to get this information

... > option 150 ip  10.10.10.1

... > dns-server   10.10.10.1 =>  private ip for dns 
... > exit 

config > "ip dhcp excluded-address 10.10.10.1" ==> private , we dont want the DHCP to assign this ip to any of the devices  ==> otherwise no 
ip to all oter phones ==> DHCP gets confused  

now let us configure the telephony service : 
... > telephony-service
...>  max-ephones 20

An ephone is an IP phone that is connected to a voice network. An ephone-dn is an extension number that can be assigned to buttons on an 
ephone. 

but why ip-phones are still used 
IP phones, also known as Voice over IP (VoIP) phones, are a popular choice for business communication. They transmit voice calls over the 
internet, eliminating the need for a separate phone line. VoIP phones can be used with existing landlines and cell phones.


...>  max-dn 20 

what is dn ? 
max-dn: Specifies the maximum number of "directory numbers "s, in the range of 1 to 200

... > ip source-address  10.10.10.1 port 2000  
... > auto assign 1 to 20 ==>  (max 20 e-phones to assign ip-address)

why 2000 port ? 
Port 2000 is used by the skinny protocol, which allows phones to communicate with Call Manager. The protocol also allows Call Manager to 
control IP phones

... > exit
... > ephone-dn 1  => to assign number to ephone-1 in format 4... 
... ephone-dn > number   401 => to assign number to ephone-1 in format 401  
... ephone-dn > ex => to exit   

... > ephone-dn 2  => to assign number to ephone-2 in format 4... 
... ephone-dn > number  402 =>  number 402 
... ephone-dn > ex => to exit   

... > ephone-dn 3  => to assign number to ephone-2 in format 4... 
... ephone-dn > number  403 =>  number 403 
... ephone-dn > ex => to exit

... => do this with ephone-dn 10 => number 410   ==> max u can do 20 (which is not working )

... > do wr => to build the dependencies finally   ==> all ip-address is distributed to the dynamic with DHCP ==> it takes time ==> vlan 
should get ip address for each of the department-voip-phones ==> a lot of time 


11 STANDARD ACL FOR SSH ==> SECURITY-RULES FOR ROUTERS  ,  i want ssh ==> MLSW's 
checking "Server-side-router" from "hr-laptop" (wireless ) => 

hr-laptop -> click -> Desktop ->cmd ->   (192.168.21.1 => ip of the server-side-router)
C: >  ssh -l cisco 192.168.21.1  ==> The -L option is used to bind a port on the local machine with a remote port at the remote destination IP 
address. , cisco is username for remote-server  ==> "REQUEST TIMED OUT  

router > do reload  ==> sometimes ip/dynamic changes takes time  , so that the images get reloaded after building dependencies ==> 
decompressing the images( all config settings)

permit only it-department as more permissions , all 10 voip phones  , 255-224 = 31 

why 31 ? ==> 0.0.0.31 is a wildcard mask that indicates the size of a network or subnet for some routing protocols, such as OSPF. To convert a 
mask from standard notation to wild card, you can subtract the subnet mask from 255.255.255.255 - 255.255.255.224 = 0.0.0.31

HQ-MLSW-config > access-list 10 permit  192.168.20.224   0.0.0.31

deny all other networks for voip-phones 
HQ-MLSW-config > access-list 10 deny any 

check/test => goto mk-LAPTOP , CLICK => desktop => cmd => 
mk-LAPTOP > ssh -l cisco 192.168.20.1 => 
password : cisco ,  => no authentication express  
" this is basically checking ssh" 

comeback to MLSW : 
HQ-MLSW-config > line vty 0 15  
why vty  ==> Virtual teletype (VTY) is a command line interface (CLI) that gives users access to a device's control plane. It's often used in 
network devices such as routers and switches.

HQ-MLSW-config  > access-class 10 in =>
" why access-class for wireless NETWORKS"
An access class (AC) controls access to network resources in wireless communication systems. The purpose is to prevent the limited bandwidth 
and capacity of wireless networks from becoming overwhelmed.

HQ-MLSW-config > exit
HQ-MLSW > do wr 

do follow these commands from "ACL" for ALL ISP'S, HQ-VOIP ,HQ-Router,  CS-MLSW, SERVER-SIDE-ROUTER 

12. PAT => port address Translation  , what is NAT first : 

NAT conserves IP addresses that are legally registered and prevents their depletion. Network address translation security. NAT offers the 
ability to access the internet with more security and privacy by hiding the device IP address from the public network, even when sending and 
receiving traffic.

pat vs vlan : 
PAT is an extension of Network Address Translation (NAT) that allows multiple devices on a LAN to be mapped to a single public IP address. PAT 
helps conserve IP addresses by assigning a single public IP to a group of hosts using different port numbers. PAT also helps improve security 
by making it more difficult for attackers to gain access to the network. 
VLAN is a concept that allows devices to be logically divided on layer 2 (data link layer). The main advantage of using VLANs is that they 
allow you to separate traffic from different users onto different segments of the same physical network switch.

HQ-router-config > int range gig0/0-1  => select the interface 0 and 1 
HQ-router-config-if-range > ip nat inside  ==> nat => network address Translation 

"IP nat inside" means that a router is inspecting incoming packets that originate from an "outside" interface and are going towards an 
"inside" interface
Translates the source IP address of packets that travel from inside to outside.

HQ-router-config-if-range > exit  

What is ip nat outside?
The "ip nat outside source" means to inspet an outgoing packet originated from an "inside" interface (configured as: ip nat inside) towards an 
"outside" interface (configured as: ip nat outside) and act accordingly.

HQ-router-config-if-range > ip nat inside 
HQ-router-config > int  se0/2/0  => select the interface serial   => single port , so no range 

HQ-router-config-if-range > ip nat outside 
HQ-router-config > int  se0/2/1  => select the interface serial  
... > exit 

create a access list for nat , pat 
HQ-router-config > access-list 50 permit 192.168.20.0   0.0.0.255

== > 192.168.20.0   0.0.0.255  ==> main-network-for-all-5 departments ==> CS, HR, LM , ... 

let us bind the above Access-List with NAT on serial interface , overload serial interface 
... > ip nat inside source list 50 interface se0/2/0 overload 
... > ip nat inside source list 50 interface se0/2/1 overload 
... > do wr => build all the dependencies 
... > do sh ip nat translations

THIS IS DONE , TO ENSURE THAT IF WE PING A DEVICE FROM HR, CS, LM ,.. => IT SHOULD PASS ITS TRAFFIC THROUGH HQ-ROUTER => may not success at 
the 1st time 
try to ping the EMAIL-SERVER through CS-PC with ipv4 ==> DONE => and check by using the command in HQ-Router 

14. SITE-SITE IP-SEC + VPN SECURE TUNNEL => MOST IMPORTANT PART , 

" first make the router licensed " => 
HQ-ROUTER > "license boot module c2900 technology-package securityK9" ==> router version is 2911, 
change the version and  "DO THIS FOR BOTH ROUTER(server-side, HQ-ROUTER) ROUTERS ==> 

HQ-ROUTER > do reload ==> to rebbot the whole device 

why site ==> 
In computer networking, the term "site" generally refers to a physical location or grouping of devices that are connected to the same network

... > access-list 110 permit ip 192.168.20.0  0.0.0.255   192.168.21.0  0.0.0.15  
==> permit all the devices from both the routers only(HQ-ROUTER), (SERVER-SIDE-ROUTER) , no hacker 
(if hacked he should do this by hacking router )

... > crypto isakmp policy 10 

... > "encryption aes 256" ==> a symmetric block cipher that the U.S. government selects to protect classified data.

====> AES IS A ENCRYPTION ALGORITHM => IT encryption uses the 256-bit key length to encrypt as well as decrypt a block of messages.

... > "authentication pre-share"   ==> A pre-shared key (PSK) is a string of characters used as an authentication key in VPNs. 

... > "group 5"   ==> n Cisco, Group 5 is the default Diffie-Hellman (DH) group, which sets the algorithm's strength in bits. Group 5 has a 
1536-bit DH key, which is considered weak. The lower the DH group number, the less CPU time is required to execute it. The higher the DH group 
number, the greater the security level

... > exit 

now make it secured , (HQ-ROUTER AND SERVER-SIDE-ROUTER TUNNEL)
what is a isakmp ?? 
==> The ISAKMP protocol is a framework for dynamically establishing security associations and cryptographic keys in an Internet environment.
... > crypto isakmp key vpnpa55 address 190.200.100.0
... > crypto ipsec transform-set VPN-SET esp-aes esp-sha-hmac 

what is esp , sha , hmac => security protocols 
ESP stands for Encapsulating Security Payload(DATA) . It's a security protocol that's part of the Internet Protocol Security (IPsec) set of 
protocols. ESP encrypts and authenticates data packets between computers using a Virtual Private Network (VPN).

... > crypto map VPN-MAP 10 ipsec-isakmp  ==> confirmation should come 
... > description VPN connection to SERVERSIDE-SITE
... > set peer 190.200.100.9  ==> JTL-ISP (IP)  ==> TO CONNECT PEER TO HQ-ROUTER 
... > set transform-set VPN-SET
... > match address 110 
... > exit 
... > interface s0/2/0
... > crypto map VPN-MAP  ==> confirmation should come 
... > exit
... > do wr 

What is the description command in Cisco?
The description command is meant to provide a reminder in the configuration to describe what certain interfaces are used for. 

transform-set in cisco ?? 
A transform set specifies the algorithms of integrity and encryption that the peer will use to protect data communications. Two peers must use the same algorithm to communicate.

match 110 ?? 
This command is used to match the IP address of the route's destination. If the destination matches the specified access list, the route is 
included in the map and processed according to the other statements in the route map. With this command, you can use extended access lists to 
implement routing policies.


SAMETHINGS FOR SERVER-SIDE-ROUTER ==> BUT REVERSE THE IP'S (SERVER-HQ ROUTING)

SERVER-SIDE-ROUTER-CONFIG > access-list 110 permit ip  192.168.21.0  0.0.0.15   192.168.20.0  0.0.0.255  
SERVER-SIDE-ROUTER-CONFIG > crypto isakmp key vpnpa55 address 190.200.100.1 
... > description VPN connection to HQ-NETWORK 
... > set peer 190.200.100.1 => HQ-Router 
