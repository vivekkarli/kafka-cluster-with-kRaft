# kafka-cluster-with-kRaft
kafka cluster setup guide with KRaft

## step: 1 install WSL2 on windows
   
- go to command prompt
  ```
  wsl --install
  ```
- restart machine

- ubuntu will be installed

- open ubuntu and setup Linux username & password


## step: 2 install java jdk 11 or higher in ubuntu

commands ....

## step: 3 install apache Kafka in ubuntu

  3.1 install latest binaries using wget commands

    wget https://downloads.apache.org/kafka/3.7.1/kafka_2.13-3.7.1.tgz

  3.2 extract the binaries

    tar xzf kafka_2.13-3.7.1.tgz 

  3.3 move kafka to the root directory

    mv kafka_2.13-3.7.0 ~

  3.4 set PATH to lauch kafka clients directly from anywhere

  - go to root directory
			```
    	cd ~
			```

  - edit .bashrc file
		```
    nano .bashrc
		```

  - go to the bottom line and add
		```
		PATH="$PATH:~/kafka_2.13-3.7.1/bin"
 		```

  - restart ubuntu
    
  - check if PATH has set properly
		```
    echo $PATH
		```
	
  - verify if kafka path is visbile

## step: 4 start kafka cluster with KRaft

4.1 disable IPv6 on WSL2, on ubuntu run
 
   ```
   sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
   sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
   ```
	
4.2 generate new cluster id

    ~/kafka_2.13-3.7.1/bin/kafka-storage.sh random-uuid

4.3 format your storage directory (replace <uuid> by the id got from above command)

    ~/kafka_2.13-3.7.1/bin/kafka-storage.sh format -t <uuid> -c ~/kafka_2.13-3.7.1/config/kraft/server.properties

4.4 And finally, start kafka cluster with KRaft

    ~/kafka_2.13-3.7.1/bin/kafka-server-start.sh ~/kafka_2.13-3.7.1/config/kraft/server.properties






