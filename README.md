Linux Networking Commands That You Must Know
--------------------------------------------

* Linux is one of the most widely used operating systems that is being used for different requirements and developments. 
* Most of us might have used it for some time in our development career. 
* While working on Linux knowing the right command saves a lot of time and headaches. 
* I generally refer to the below article to find commands that I use most frequently.


### 1. ifconfig

* `ifconfig` — Interface configurator.

* This command is used to display the route and the network interface. 
* It can also be used for initializing an interface, configuring it with an IP address, and enabling or disabling it.
```
ifconfig
```


### 2. traceroute

* `traceroute` — Used for troubleshooting the network. 
* It detects the delay and determines the pathway to the specified target.

* It provides the names and identifies every device on the path.
* It follows the route to the destination
* It determines where the network latency comes from and reports it.
```
traceroute <destination>
```

* Note : If you don’t have the traceroute service installed in your system, you can install it using the following command:
```
sudo apt-get install inetutils-traceroute
```

* Command: `traceroute google.com`

* The output of the above command will have the following information: the specified hostname, the size of the packets, the maximum number of hops required, and the IP address.

* Note: To avoid the reverse DNS lookup, add -n in the command syntax.

* Command: `traceroute -n google.com`

* The output indicates network delays. 
* The asterisks shown in the output indicate a potential problem in reaching that host. 
* They indicate packet loss during communication to the network.

* Generally, the traceroute command sends UDP packets. 
* It can as well send TCP or ICMP packets.

* To specifically send in ICMP, use this,

* Command: `traceroute -I google.com`

* To send a variant of TCP, use this,

* Command: `traceroute -T google.com`


### 3. tracepath

* `tracepath` — similar to the traceroute command.

* It is used to detect network delays. 
* However, it doesn’t require root privileges and is installed in Ubuntu by default.

* It traces the route to the specified destination and identifies each hop in it. 
* If your network is weak, it recognizes the point where the network is weak.
```
tracepath <destination>
```

* Example: `tracepath google.com`


### 4. ping

* Linux ping is one of the most used network troubleshooting commands. 
* It checks for network connectivity between two nodes.

* ping stands for Packet INternet Groper.

* The ping command sends the ICMP echo request to check the network connectivity. 
* It keeps executing until it is interrupted. We can use the ctrl+c key to interrupt the execution.
```
ping <destination>
```

* Example : `ping google.com`

* We can also use the IP address to ping directly. 
* We can limit the number of packets by including “-c” in the ping command.
```
ping -c <number> <destination>
```


### 5. netstat

* Linux netstat command refers to the network statistics.

* It provides statistical figures about different interfaces which include open sockets, routing tables, and connection information.
```
netstat
```

* Output:
```
vikram@100200300 ~ % netstat
Active Internet connections
Proto  Recv-Q  Send-Q  Local Address    Foreign Address (state)
tcp4   0       0       1.2.3.4.5865     4.3.2.1.https ESTABLISHED
tcp4   0       0       1.100.1.3.542    1.40.1.17.18903 SYN_SENT
```
Observe the output displaying all the open sockets.

* Variations in netstat command:
    * Below are a few variations of the netstat command used.


* To display the programs, use below
``` 
netstat -p
```

* To get the details of the ports, use below
```
netstat -s
```

* This gives detailed statistics of all the ports.

* To get the information of the routing table, use below
```
netstat -r
```

* This gives information related to the routing table.


### 6. hostname

* Linux hostname is the simple command used to view and set the hostname of a system.
```
hostname
```

* To set the hostname —
    * Use the syntax below to set the hostname.
```
sudo hostname <newName>
```

* The hostname set through this command is not permanent. 
* It will be reset to the name in the hostname file back when the system reboots.

* To permanently set a hostname, you have to re-write the hostname in the hostname file, present on the server. Once set, you have to reboot the box.

* In Ubuntu, /etc/hostname file is used.
* In RHEL, /etc/sysconfig/network is used.


### 7. curl

* curl is a command-line tool to transfer data to or from a server, using any of the supported protocols (HTTP, FTP, IMAP, POP3, SCP, SFTP, SMTP, TFTP, TELNET, LDAP, or FILE).

* curl:
```
curl [options] [URL…]
```

* Example:
* The most basic use of curl is typing the command followed by the URL.
```
curl https://www.google.com
```

* This displays the content of the URL on the terminal. 
* The URL syntax is protocol dependent and multiple URLs can be written as sets like:
```
curl http://example.{one, two, three}.com
```

* URLs with numeric sequence series can be written as:
```
curl ftp://ftp.example.com/file[1-20].jpeg
```

* The below Options can be used with the curl command:
* `o`: using this flag we can save the downloaded file on the local machine with the name provided as the parameters.
```
curl -o [file_name] [URL...]
```

* Example:
```
curl -o curl_file.html https://www.google.com
```


### 8. wget

* wget is a command-line utility for downloading files from the web.
* With wget, you can download files using HTTP, HTTPS, and FTP protocols.
* wget provides several options allowing you to download multiple files, resume downloads, limit the bandwidth, recursive downloads, download in the background, mirror a website, and much more.
```
wget [option] [URL]
```

* Let’s see some examples:
    * To simply download a webpage:
```
wget http://eg.com/sample.html
```

* To download the file in the background:
```
wget -b http://www.eg.com/sample.html
```

* To overwrite the log while downloading the file using the wget command:
```
wget http://www.eg.com/samplefile.txt -O /path/samplefile.txt
```

* Resume a partially downloaded file:
```
wget -c http://example.com/samplefile.tar.gz
```

* To try a given number of times:
```
wget --tries=10 http://eg.com/samplefile.tar.gz
```


### 9. whois

* Linux whois command is used to fetch all the information related to a website. 
* You can get all the information about a website including the registration and the owner information.
```
whois <websiteName>
```

* Example:`whois google.com`


### 10. scp

* SCP (secure copy) is a command-line utility that allows you to securely copy files and directories between two locations.

* With scp, you can copy a file or directory:

* From your local system to a remote system.
* From a remote system to your local system.
* Between two remote systems from your local system.
* When transferring data with scp, both the files and password are encrypted so that anyone snooping on the traffic doesn’t get anything sensitive.

* SCP Command Syntax:
    * Let’s review the basic syntax of the scp command.
```
scp [OPTION] user@src_host:file_name1 user@dest_host:file_name2
```

* `OPTION` - scp options such as cipher, ssh configuration, ssh port, limit, recursive copy, etc.

* Local files should be specified using an absolute or relative path, while remote file names should include a user and host specification.

* scp provides several options that control every aspect of its behavior. The most widely used options are:

* `-i` — Identity_file
    * Selects the file from which the identity (private key) for public-key authentication is read. This option is directly passed to ssh(1).
* `-r` - This option tells scp to copy directories recursively.


### 11. ssh

* ssh stands for Secure Shell. 
* It is a protocol used to securely connect to a remote server/system. 
* ssh is secure in the sense that it transfers the data in encrypted form between the host and the client. 
* It transfers inputs from the client to the host and relays back the output. 
* `ssh` runs at `TCP/IP port 22`.
```
ssh user_name@host(IP/Domain_name)
```

* Example: `ssh -i ~/pk.pem root@1.2.3.4`

* The i flag — To use a private key for a specified hostname and not the default ssh key that is located in ~/.ssh

* THANK YOU FOR READING!

![Preview](Images/Thankyou%20.png)