### Enable JNLP port
1. Go to Manage Jenkin `http://18.191.185.219:8080/manage`
2. Select `Configure Global Security`
3. Under `Agents`, select `Fixed` and add `50000`. Click `Save`

### Install agent using `Launch agent by connecting it to the master`
1. Go to Jenkins dashboard `http://18.191.185.219:8080/`
2. Click `Build Executor Status`
3. Select `New Node`
4. Add `Node Name` as `windows_node` & Select `Permanent Agent`. Click `OK`
5. Add `Description` as `This is Windows Node`, `Number of executors` as `1`, `Remote root directory` as `C:\training\jenkins`, `Labels` as `windows`
6. Add `Usage` as `Only build jobs with labels expression matching this node`
7. Add `Launch Method` as `Launch agent by connecting it to the master`
8. Keep other options as `Deafult`. Click `Save`

### Once completed one offline node is avaiable under `Build Executor Status`

1. Select `Windows Nodes` which is showing offline
2. Ensure Java is installed on the node
3. Access `http://18.191.185.219:8080/jnlpJars/agent.jar` to donwload `agent.jar` and place it in agent remote direectory which is `C:\training\jenkins`
4. Open `CMD` & Run `cd c:\training\jenkins`
5. Copy command under `Run from agent command line:` and Runthe same from CMD
