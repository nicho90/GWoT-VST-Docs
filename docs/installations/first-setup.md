## What to do?

1) Connect via SSH to Linux-Machine (Server):
	
```
ssh giv-gwot-vst.uni-muenster.de
```	
	
2) Change User-Password with the command: 
	
```
passwd
```
	
3) Installation of **git**

```bash
sudo apt-get install git
```

4) Cloning repositories
	
**GWoT-VST**
	
```bash
git clone https://github.com/nicho90/GWoT-VST.git
```
	
**GWoT-VST-Docs**
	
```bash
git clone https://github.com/nicho90/GWoT-VST-Docs.git
```

5) Installation of **nodejs**

	Please follow the steps of this [installation guide](/installations/nodejs).
	
6) Installation of all dependecies (node-packages or node-modules)

```bash
cd /home/n_schi16/GWoT-VST/server
npm install
```

Check if all dependecies of the `package.json`-file were successfully installed in the folder `/node_modules`. Use `cat package.json` to get a preview of the file and check with the following command 

7) Installation of forever-package

Please follow the steps of this [installation guide](/installations/running).
	
