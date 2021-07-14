### KAMIKAZE - Deployment Control Plane

### AuthN and AuthZ
To get access to kamikaze, Please use the following CAM profiles:
readonly(User can view everything but cannot take any action) - No need of any CAM profile
operator(User can view everything, trigger actions like deploy/config and start/stop/skip actions.) - SAPSF_GLOBAL_CICD_Tools_Operator
admin(superuser status, can login to admin portal and edit) - SAPSF_GLOBAL_CICD_Tools_Admin

CAM profile:
Name : SAPSF_GLOBAL_CICD_Tools
 
Access Levels:
SAPSF_GLOBAL_CICD_Tools_Admin
SAPSF_GLOBAL_CICD_Tools_Operator
SAPSF_GLOBAL_CICD_Tools_Monitor

## Exception Handling

1. Every job has retry option available via action definition which is bootstrapped during application start up.
    
    'name' : 'implement_cr',
    'weight' : 5,
    'retries' : 1

2. During tomcat deplooyment, if deployment failure rate is more than 75%, deployment will be retriggered until retries are exhausted.
3. During tomcat deployment, if deployment fails due to connectivity error between rundeck and the target node, it will be mitigated by rebootstrapping the node to chef server.
4. During Tomcat deployment, if deployment failure rate is less than 25%, deployment will be triggered on these nodes after verifying the health of the node.
5. If rundeck is not able to connect to the node, Service Now incident will be created so AGC team can check and reboot the node if required.
6. During web deployment, deployment will be retriggered until retries are exhausted.
7. During web deployment, if deployment fails due to space issue, kamikaze will try to search files which are similar to provided build pattern and delete them.
# AZ-204
