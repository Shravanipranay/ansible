# Call ansible playbook for java in azure devops (Self hosted) ACN

* For this you need create self hosted agent.
    1. Lets configure a self hosted agent.
    2. Create a ubuntu vm(version 20)
    3. Lets try to build this application
    4. Self Hosted agents can be created in custom pools or default pool
 1. Login to azure devops
 2. navigate agent pools
 3. Navigate to default
 4. Click on new agent
 
 In Terminal

* make directory myagent [Mkdir myagent]
* cd myagent
* Download the file from azure devops by using wget command.
* Extract the file tar -zxvf
* ./config
For configuration we need to create token.
[refer] https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops#permissions
* ./run.sh


## In azure devops

* Craete one file with the ansible playbook script and create one host file in that give localhost.
* Run pipeline for java from ansible playbook

# Pipeline
```

---
pool:
  name: 'Default'
trigger:
- main

steps:
 - script: ansible-playbook -i hosts javamultiver.yaml
   displayName: Running_java
   workingDirectory: /ansible.git/java
```

* In working directory give the path where the yaml file is located.

  





