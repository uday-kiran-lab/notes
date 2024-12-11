what is server?
server having lot many services.
each service have it's separate protocol.
each server having 65,536 ports (0 to 65535).
some examples of protocols and their defualt ports are 
SSH -- 22
HTTP -- 80
HTTPS -- 443
mysql --- 3306
we are using SSH protocol is used to connect the server.
connecting server we need following parameters.
1.protocol
2.port number
3.username
4.password/private-key
  for genrate keys below command need to use
  ssh-keygen -f <filename> 
  ##ssh-keygen -f linux_keys
It will genrate public key with extension of .pub
public key is follwing below fomrat.
ssh-rsa <random _code> laptop_username@laptop_name
Note: filename should be in small case
while connecting server we need clients. some clients are listed below
gitbash --> we can use as git, linux server and mini Linux in windows
* By defualt we are launchued to home directory
putty
mobaxtrem

steps:

a) genrate public key and private key
-------------------------------------
1. install gitbash
2. craete folder in desktop/laptop
3. navigate that folder in gitbash by using cd command
4. generate keys by using ssh-keygen -f <filename>
ex: ssh-keygen -f linux_keys

b) add public key to server/instance
-------------------------------------
1. create aws account and login to aws console
2. search EC2 intances and go to network& security
3. select key pair and click on actions and select import key pair
4. give some name (daws-81s), paste the public key under description(public key present in .pub file)
5. click on import key

c) create security group/firewall system
------------------------------------------
security group is allows the authorized ports only.
1. click on security group and fill name as allow-ssh and provide description
2. add inbound rule and select type as SSH and select the network notation
    0.0.0.0/0 defines public can access
3. click on create security group

d) creating server/instance
----------------------------
1. goto EC2 and click on launch instance
2. give some name for instance
3. select os as amazon-linux 2023 and select instance type as t2micro
4. select key-pair as created above (daws-81s)
5. select security group as created above(allow-ssh)
6. remaining all keep same and click on launch instance

--still now we are created server in aws 
--now we are connected to server through ssh in gitbash
$ ssh -i <private_key_file> <username>@ip.address
by defualt aws instanec username as ec2-user
ip-address copied from aws insatnce(use public-ip)
$ ssh -i linux_key.pem ec2-user@public-ipaddress




