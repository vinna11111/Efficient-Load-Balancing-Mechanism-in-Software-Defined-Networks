# Efficient-Load-Balancing-Mechanism-in-Software-Defined-Networks
Required libraries and packages:
•	Python3.10+
•	Mininet
•	Xterm
•	requests (python library) in virtual environment
o	WE MAY NEED TO START ANOTHER TERMINAL TO INSTALL THE PYTHON LIBRARIES IN VIRTUAL. IT WILL NOT WORK IN MININET NODES
o	FOR THIS ALSO WE NEED TO GET IN PYTHON ENV WITH BELOW MENTIONED COMMAND
Approach to write the code
Complete Code is the standard code given as a default load balancer by pox in the “pox/pox/misc” by the name of ip_loadbalancer. This load balancer is a random load balancer. For other load balancer just _pick_server method is changed and some class variable of iplb class are added
Where to find the code
{R}/project/pox/pox/misc is the directory to find all the code for load balancers
Below are the names:
•	load_balancer_resp_time
•	load_balancer_round_robin
•	load_balancer_random

Algorithm used for response time load balancer:
Weighted round robin according to the response time. Lesser the response time more the weight for the server
Lets response time for the 2 servers be a and b
Then weight for the servers be a*b/a and a*b/b reduced to the single digit ratios be p and q respectively
Now it will go in the round robin fashion as first p requests to server 1 then q requests to server 2 and then p requests to server 1 and so on…
How to run and test the code
Step1: Open the terminal change to project directory as  {R}/project
Step2: Open mininet with the command “sudo mn –topo single,6 –controller=remote,port=6633”
Step3: Open three nodes in mininet environment with “xterm h1 h2 h3”
Step4: Here h1 and h2 will act as servers. Enter python virtual environment in both the nodes h1 and h2 with “source env/bin/activate” in both the node
Step5: open the server with “python server_simulation_1.py” and “python server_simulation_2.py” respectively in both the node.
IF SERVER DOES NOT START KINDLY INSTALL ALL THE MISSING LIBRARIES
Step6: Now the servers are active on 10.0.0.1 and 10.0.0.2
Step7: Start the load balancer. We need sudo access for this.
Step8: Getting sudo access to start load balancer
	Sudo -i
	Enter the password
	cd ../home/{user_name}/{R/project/pox
Step9: Starting load balancer
	{python or python3} pox.py log.level  –DEBUG misc.{load balancer name}  –ip=10.0.1.1 –serves=10.0.0.1,10.0.0.2 

This will directly the load balancer for the round robin and random algorithm load balancer but for the response time load balancer it will ask for the average response time of the servers.
Step10: Hitting requests to the load balancer in node h3 h4 h5 
	We can use curl, nc or even make our code to test thee load balancer 
	REQUEST SHOHULD BE MADE TO LOAD BALANCER IP NOT ON SERVER’S IP

