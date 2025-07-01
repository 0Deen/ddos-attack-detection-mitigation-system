# I. Server Administration Information:
## VMware:
Product: VMware® Workstation 15 Pro  
Version: 15.5.0 build-14665864  
## Ryu Controller:
OS: Ubuntu 19.10 eoan  
IP: 192.168.0.104   
## Mininet:
OS: Ubuntu 18.04.6 LTS  
IP:192.168.0.100


# II. Build SDN System
## 1. Ryu Controller
**Step 1: Goto my project**
```sh
cd my_project/controller/
```
**Step 2: Start Controller SDN**  
In this directory, I have created multiple Controller files, each corresponding to different machine learning algorithms used for testing in various scenarios of detecting and mitigating DDoS attacks. Specifically:
- DT_controller-detect.py: this file uses a Decision Tree algorithm so the system can detect DDoS attacks.
- KNN_controller-detech.py: uses a K-Nearest Neighbors algorithm. algorithm so the system can detect DDoS attacks.
- RF_controller.py: uses a Randowm Forest algorithm. algorithm so the system can detect DDoS attacks.
- DTree_Controller.py: this file uses a Decision Tree algorithm so the system can detect and mitigate DDoS attacks.
- KNN_Controller.py: uses a K-Nearest Neighbors algorithm so the system can detect and mitigate DDoS attacks.

Controller normal (The controller operates normally and does not have an integrated attack detection and mitigation module):
```sh
ryu-manager ryu.app.simple_switch_13,ryu.app.ofctl_rest flowmanager/flowmanager.py    --observe-links --ofp-tcp-listen-port 6653 --wsapi-port 8080"
```
Controller detect:
```sh
DTree: ryu-manager DT_controller-detect.py,ryu.app.ofctl_rest flowmanager/flowmanager.py  --observe-links --ofp-tcp-listen-port 6653 --wsapi-port 8080
KNN:   ryu-manager KNN_controller-detech.py,ryu.app.ofctl_rest flowmanager/flowmanager.py  --observe-links --ofp-tcp-listen-port 6653 --wsapi-port 8080
```
Controller detect & mitigation:
```sh
DTree: ryu-manager DTree_Controller.py,ryu.app.ofctl_rest flowmanager/flowmanager.py  --observe-links --ofp-tcp-listen-port 6653 --wsapi-port 8080
KNN:   ryu-manager KNN_Controller.py,ryu.app.ofctl_rest flowmanager/flowmanager.py  --observe-links --ofp-tcp-listen-port 6653 --wsapi-port 8080
```
**Step 3: Controller management site**
```sh
http://192.168.0.104:8080/home/index.html
```
		
## 2. Mininet
**Step 1: Goto my project**
```sh
cd project/mininet
```
**Step 2: Start sflow service**
```sh
sudo ./sflow/sflow-rt/start.sh
```
After starting sflow, you should open another command line on linux to initialize mininet

**Step 3: Start mininet**  
Within the scope of my experiment, I created 2 mininet files in python3 language. Furthermore, I use the command in linux to create mininet virtual devices, details are as below:
- Topology 1: 12 hosts and 6 switches
```sh
sudo mn --custom topology.py,sflow/sflow-rt/extras/sflow.py --link tc,bw=10 --controller=remote,ip=192.168.0.104:6653 --topo mytopo
```
- Topology 2: 6 hosts and 3 switches
```sh
sudo mn --custom topology2.py,sflow/sflow-rt/extras/sflow.py --controller=remote,ip=192.168.0.104:6653 --topo mytopo
