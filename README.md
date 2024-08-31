# Network_Catch_Maltrails
Maltrail IDs are unique identifiers for threats detected by Maltrail. They provide information like threat type, severity, source/destination IP/port, and timestamps. This data helps security analysts understand and analyze malicious traffic patterns.


<img width="215" alt="image" src="https://github.com/user-attachments/assets/8182effc-b834-4633-a820-f39dc7416561">


Maltrail is a malicious traffic detection system, utilizing publicly available (black)lists containing malicious and/or generally suspicious trails, along with static trails compiled from various AV reports and custom user-defined lists, where trail can be anything from domain name, URL, IP address . ( MTDS ) . It is a threat hunting tool

Maintain the Process Follow As Line Mentioned (Any mistake may issue with connection)*
OS Type : Linux : Kali 


1st Segment

    sudo apt-get install git python3 python3-dev python3-pip python-is-python3 libpcap-dev build-essential procps schedtool
    sudo pip3 install pcapy-ng
    cd /tmp
    git clone --depth 1 https://github.com/stamparm/maltrail.git
    sudo mv /tmp/maltrail /opt
      sudo chown -R $USER:$USER /opt/maltrail

2nd Segment

      sudo mkdir -p /var/log/maltrail
    sudo mkdir -p /etc/maltrail
    sudo cp /opt/maltrail/maltrail.conf /etc/maltrail
    sudo nano /etc/maltrail/maltrail.conf

3rd Segment


After entering the maltrail.conf file as mention this line ( sudo nano /etc/maltrail/maltrail.conf ) . At the end need to setup of some rules as mention details under with green line. As shown make as same 

    crontab -e
    */5 * * * * if [ -n "$(ps -ef | grep -v grep | grep 'server.py')" ]; then : ; else python3 /opt/maltrail/server.py -c /etc/maltrail/maltrail.conf; fi0 1 * * * cd /opt/maltrail && git pull


    crontab -e
    */1 * * * * if [ -n "$(ps -ef | grep -v grep | grep 'sensor.py')" ]; then : ; else python3 /opt/maltrail/sensor.py -c /etc/maltrail/maltrail.conf; fi2 1 * * * /usr/bin/pkill -f maltrail


4th Segment

    sudo cp /opt/maltrail/maltrail-sensor.service /etc/systemd/system/maltrail-sensor.service
    sudo cp /opt/maltrail/maltrail-server.service /etc/systemd/system/maltrail-server.service
        sudo systemctl daemon-reload
        sudo systemctl start maltrail-server.service
            sudo systemctl start maltrail-sensor.service
    sudo systemctl enable maltrail-server.service
        sudo systemctl enable maltrail-sensor.service
                    systemctl status maltrail-server.service && systemctl status maltrail-sensor.service


After Doing all four segments 

Check ip address of your host machine with this command
Ifconfig 				open with another terminal

After all four segment : DONE , it means that the dashboard has been generated against with the host machine HTTP Server
Example : http://0.0.0.0:8339/ or 0.0.0.0:8338 or (VirtualHOST_IP:8339) 
Enter of your host ip on VirtualHOST_IP
In mention example run the server dashboard for monitoring

You see the dialogue box that notify to proceed with authentication
	<img width="204" alt="image" src="https://github.com/user-attachments/assets/1146c3c9-2b1d-4c58-b6c8-605ace9f4f9e"> 	Username : admin
							                                                                                                Password : changeme!
						        
After all done with authentication you see some thing like that :
<img width="491" alt="image" src="https://github.com/user-attachments/assets/772b3c3b-6479-4eba-89e6-7fbb395402ac">


Testing Phase 1


If you have another browser of same system , open as Edge , chrome , Firefox ,etc


Open new terminal 
At first mention below code be type as it is in notepad 

    nslookup morphed.ru
    cat /var/log/maltrail/$(date +”%Y-%m-%d”).log

After doing 1st trial run successfully and check on dashboard and make refresh the website server.


<img width="489" alt="image" src="https://github.com/user-attachments/assets/dbf3adc8-e095-4db9-8633-9b1fc18e9a79">
        #This code Severity level is : HIGH
        #Trail : morphed.ru
        #Reference : Static 
        #Type : DNS

It Means that it run : Well !!


Test Phase 2

Search : Any Iplocation service as ip2location
Enter your ip on there and click for lookup.

This test define that if you search your ip for iplocation. It work on diagram below

VirtualHOST_IP -> ip2location -> ip2location server that based in any where ->

BounceBack -> VirtualHOST_IP
Maltrail sense the pixel dot
Location tracking of any ip as known as suspect listing

Test Phase 3

Open a new OS
Setup a VPN Connection as openvpn
You can get openvpn config file from (TRYHACKME)

It define another ipmachine that define from outsource test

Generate Ping test 

Some Testing (MENTION_IP) , replace on (MENTION_IP) below main code

    192.42.116.175
        192.42.116.219
    185.220.100.243


Caution dont try this ip’s on HOST_MACHINE , It may damaged or Trojan or Malicious activity possibility
Test some malicious IP Looping Reverse Thread ( IPLRT )

    ping -c 1 (MENTION_IP)
    cat /var/log/maltrail/$(date +”%Y-%m-%d”).log

Type this code on notepad as it is …………

Geolocation is under 			    : UDP Protocol ( Transport Layer )
Ping based service is under 		: ICMP Protocol ( Network Layer )
Nmap , attack is under 		        : TCP Protocol ( Transport Layer )
DDos attck is under                 : HTTP (application layer attacks) | TCP/IP (network layer attacks)

Test Phase 4

Check above ip’s on VIRUSTOTAL website




There are many way to can test of malicious traffic on system



