# Introduction
- Probius: Automated Approach for VNF and Service Chain Analysis in Software-Defined NFV  

# Notification
- If you find any bugs or have some questions, please send an e-mail to us.  

# Configuration
- The configuration of the Probius system: config/global.conf  
- The configurations of VNFs: config/vnf.conf  
- Service chain policies: config/policy.conf  

# Test environment
- The current Probius is fully tested on Ubuntu 16.04.  
- It may work on other Linux platforms if its dependency issues are solved.  

# Requirement
- Psutil version = 1.2.1  
- Three machines are required to run Probius  
- Traffic generator (sender) - Probius - Traffic generator (receiver)  

# Probius Installation
1. Clone the NFV platform for service chaining  
Probius $ cd ~  
Probius $ git clone https://github.com/sdx4u/sfc  
1. Set up the framework  
Probius $ cd sfc  
Follow the instructions in the README file  
2. Clone the source codes of Probius  
Probius $ cd ~  
Probius $ git clone https://github.com/sdx4u/probius    
3. Install dependencies  
Probius $ cd ~/probius/setup  
Probius $ ./deps.sh  
Probius $ sudo reboot  
4. Modify the configurations for Probius  
Probius $ cd ~/probius/config  
Probius $ vi global.conf  
Probius $ vi vnf.conf  
Probius $ vi policy.conf  

# Traffic Generator Installation
1. Clone the source codes of Probius  
TG $ cd ~  
TG $ git clone https://github.com/sdx4u/probius  
2. Make the symbolic link of 'workloads' directory  
TG $ ln -s ~/probius/workloads  
3. Install dependencies  
TG $ cd ~/workloads  
TG $ ./deps.sh  
4. Push SSH keys to each traffic generator in order to log it in without password  
Probius $ cd ~/probius/util  
Probius $ ./push-key.sh [userID]@[traffic generator IP address]  
5. Modify the configurations for traffic generator  
Probius $ cd ~/probius/config  
Probius $ vi global.conf  

# Execution
- Analyze single VNFs  
$ ./1\_analysis.py vnf  
- Analyze service chains with the specific number of VNFs  
$ ./1\_analysis.py sc [# of VNFs]  
- Analyze a specific service chain  
$ ./1\_analysis.py case [VNF1,VNF2,VNF3,...]  

- Detect performance anomaly  
$ ./2\_anomaly.py  

- Get the details of a suspicious service chain  
$ ./3\_report.py all  
$ ./3\_report.py [VNF1,VNF2,VNF3, ...]  

- Draw state transition graphs for a suspicious service chain  
$ ./4\_graph.py [VNF1,VNF2,VNF3, ...]  

- Reset the database and other logs of the Probius  
$ ./clean.sh  

- CAUSION!  
Please make sure that you have changed configuration files in the 'config' directory for your environment!  

# Author
- Jaehyun Nam <namjh@kaist.ac.kr>  

# Contributor
- Junsik Seo <js0780@kaist.ac.kr>  
