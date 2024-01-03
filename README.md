# Ansible_Course

## To create Inventory file used ip address from lxc containters  
More information about lxc click [here](https://linuxcontainers.org/)

## Testing communication with groups of hosts
	
### Checking ssh connection to hosts in a group
ansible database -m ping -u root -i inventory -> databse - group of hosts, ping - command, root - user, inventory - inventor file containing groupe
	
The result of the command:
	root@vagrant:/home/panda/course/Ansible_Course# ansible database -m ping -u root -i inventory
	10.0.3.156 | SUCCESS => {
		"ansible_facts": {
			"discovered_interpreter_python": "/usr/bin/python3"
		},
		"changed": false,
		"ping": "pong"
	}
	
### Lecture command to be executed in defined containers:
ansible web -a "free -m" -i inventory -> web - hosts group, -a "command to execute on hosts" -a "command to execute on hosts" -a "hosts inventor file
	
The result of the command:
	root@vagrant:/home/panda/course/Ansible_Course# ansible web -a "free -m" -i inventory
	10.0.3.7 | CHANGED | rc=0 >>
				  total        used        free      shared  buff/cache   available
	Mem:           9941          40        9849           0          51        9901
	Swap:             0           0           0
	10.0.3.248 | CHANGED | rc=0 >>
				  total        used        free      shared  buff/cache   available
	Mem:           9941          40        9849           0          52        9901
	Swap:             0           0           0
		
### A command that aims to update servers:
		
The result of the command:
	root@vagrant:/home/panda/course/Ansible_Course# ansible servers -a "apt-get update" -i inventory -u root -> servers - grupa serwerow, -a "komenda do wykonania", -i plik_inwentarza, -u uzytkownik
	10.0.3.248 | CHANGED | rc=0 >>
	Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
	Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
	Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
	Fetched 114 kB in 1s (82.7 kB/s)
	Reading package lists...
	10.0.3.7 | CHANGED | rc=0 >>
	Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
	Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
	Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
	Fetched 114 kB in 1s (85.6 kB/s)
	Reading package lists...
	10.0.3.156 | CHANGED | rc=0 >>
	Hit:1 http://security.ubuntu.com/ubuntu focal-security InRelease
	Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease
	Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
	Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [3,021 kB]
	Get:5 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1,141 kB]
	Fetched 4,276 kB in 7s (580 kB/s)
	Reading package lists...