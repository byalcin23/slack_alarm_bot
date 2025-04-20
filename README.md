:rotating_light: Slack Log Alert Script for OpenShift Deployments
This Python script monitors OpenShift deployment logs and sends lines containing |ERROR| to a specified Slack channel.

:sparkles: Features
:mag: Filters OpenShift deployments by name (e.g., those containing "vbu")

:clock1: Fetches logs from the last 60 minutes

:warning: Searches logs for lines containing |ERROR|

:speech_balloon: Sends alerts to a Slack channel via bot token

:gear: Setup and Configuration
Update the following variables in the script:

CAHNNEL_ID = Slack channel ID
BEARER_TOKEN = Slack bot token, e.g., 'Bearer xxxxx-xxxxx'

Replace placeholders in the OpenShift login command:

oc login --server=OCP_SERVER_API_HERE -u USER_NAME -p "PASSWRD"

Ensure this directory structure exists:

/products/scripts/slack_alarm_sender/
├── slack_log_alert.py
└── logs/

:package: Requirements
Python 3.x

OpenShift CLI (oc) installed and in PATH

Python requests module installed

To install the required Python package:
pip install requests

:rocket: Usage
Run the script manually:
python3 slack_log_alert.py

Or schedule it using a cronjob or any job scheduler.

:memo: Output
If an error is found in the logs, the script sends a Slack message like:

ERROR VEREN SERVİS: <deployment_name>
<error_line>

:lock: Security Notes
Do not hardcode sensitive data (tokens, passwords) into the script.

Use environment variables or a secure secret manager.

Limit access to the logs directory as it may contain sensitive data.

:wrench: Improvements To-Do
 Replace os.system() with subprocess.run() for better security and control

 Load configuration from a .env file or external config

 Improve error handling

 Add more advanced filtering for logs

:bust_in_silhouette: Author
Originally developed by Bahadır during his time at Vodafone.
Shared for educational and operational use.
