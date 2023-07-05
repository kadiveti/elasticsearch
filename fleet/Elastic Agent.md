# Installing Elastic Agent
------------
Elastic Agent is a unified tool that allows you to easily add monitoring capabilities to a host, including logs, metrics, and other data types. It can also provide security protection and query data from operating systems. With Elastic Agent, you can deploy monitoring across your infrastructure quickly and efficiently. Each agent has a policy that can be updated to add new integrations for different data sources and security features.


### Steps to Install Elastic Agent

##### Step1:

Navigate to Management Tab ⇒ Select Fleet

![image](https://github.com/kadiveti/elasticsearch/assets/26748605/90e6bf61-62c8-4cde-bc21-1697527cdd1d)

##### Step2:

Go to Agent Policy ⇒ Add Create Agent Policy

![image](https://github.com/kadiveti/elasticsearch/assets/26748605/f0da93b2-3aea-4c5f-ad44-40e8726a4c82)

Give a name to the policy that will be applied to multiple agents. 

Create AgentPolicy 

<img width="494" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/6f1a35bc-f75a-461a-851f-c07beafa60dc">


##### Step3:
By default system integrations are tagged to the policy. You can add or remove the integration needed for your usecase.

Select Add Integration (300 + Integrations are avaible) --> Add Integration( Here i selected Windows)

<img width="946" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/fa0120df-f6eb-4e77-9806-596b910c9eba">

Add Windows --> Make the changes if you need any --> Save and continue

##### Step4:

By default, it will create an enrollment Token.

You can create one and assign it to a policy.

<img width="284" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/bce64e96-ba87-4da2-9218-8da50c7babac">

##### Step5:

Add the agent

<img width="941" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/4e0e5edc-efbf-46d6-a94d-d42122e2a6a7">

Add the policy to which the agent needs to be tagged.

<img width="464" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/d75ae572-cce9-438e-8af5-541ee15b9437">

Select the OS which you want to deploy.

<img width="430" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/ea1c3c28-55e0-44d9-8583-9b87624d930d">

Open Powershell.

Paste the command copied from the Kibana.

<img width="663" alt="image" src="https://github.com/kadiveti/elasticsearch/assets/26748605/aeb855e0-e2f8-478a-a65f-9eae09a44247">

It will show the below.

Elastic Agent has been successfully installed.

##### Step6:

If you want to update or delete the data it is sending you can update from the Data Stream.







