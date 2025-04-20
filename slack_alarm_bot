import requests
import json
import os
CAHNNEL_ID= #CHANNEL ID HERE
BEARER_TOKEN= #TOKEN HERE      ex.'Bearer xjsnjssd-asda-asd'

def send_message (message):
  url = "https://slack.com/api/chat.postMessage"
  payload = json.dumps({
    "channel": CAHNNEL_ID,
    "text": message
  })
  headers = {
    'Content-type': 'application/json',
    'Authorization': BEARER_TOKEN
  }
  response = requests.request("POST", url, headers=headers, data=payload)

#extract log
os.system('rm -rf /home/test_user/.kube/config')
os.system('oc login --server=####OCP_SERVER_API_HERE#### --insecure-skip-tls-verify=true -u USER_NAME -p "PASSWRD"')
os.system('oc project ####PROJECT####')
deploymen_configs = os.popen('oc get deployment -o custom-columns=":metadata.name" | grep vbu').read().split() #Filter deployment
for dc in deploymen_configs:
  prep_sh="oc logs --since 60m deployment/"+dc+"  > /products/scripts/slack_alarm_sender/logs/"+dc+""
  os.system(prep_sh)
  # print(dc)
log_files = os.popen("ls /products/scripts/slack_alarm_sender/logs").read().split()
for file in log_files:
  with open('/products/scripts/slack_alarm_sender/logs/'+file+'', encoding="utf8") as f:
      f = f.readlines()
  for line in f:
    if "|ERROR|" in line: #If find |ERROR| in any line off pod logs send to slack alarm
      # print("error veren line "+line)
      send_message("*ERROR VEREN SERVİS*: "+file+"\n"+"```"+line+"```")
    else:
      print(file+"  : Temiz")
