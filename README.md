Run python application in EC2 instance to grab data from API, do some transformation, normilaze data from nested json to dataframe and then upload to s3 bucket.


1. Scenario
You are going to get the job data from an API. Please go to the API web page first (https://www.themuse.com/developers/api/v2), and take a look at the page. We will use Page 50 for this lab. So, let’s go to Job, and input 50 in the “page” field, and leave other fields blank.

2. Detail Steps
Create an EC2 Instance on AWS.
Build your python Project on EC2 via VSCode. (You need VSCode remotely SSH connect to EC2)
Use the python script to read the API (use **requests library)**
Get the data we want:

“company name”
“locations”,
“job name”,
“job type”,
“publication date”,
Convert the json data into a dataframe (use pandas library)

Manipulate data: create a table include:

company_name
country (cut the string of “locations”, keep the country part)
city (cut the string of “locations”, keep the city part)
Job_name
Job_type
Date (cut string of “publication date” only keep date part)

Save the data into S3 bucket.


3. Requirements
In the project (one-off project), the files include:

A shell script to set your virtual environment
.gitignore file
A python run script
A toml file if you need to config parameters
A separate file to save your secrets
Better to initiate your project environment with a shell script.
Better to use a shell script to control the python script.

1. set all secrets in .env
2. set all config in config.toml
3. run **init.sh** to create a virtual environment
4. the python script enbeded in **run.sh**, and use **run.sh**  to control job
5. there are two versions of python script:
    - run_v1.py: A regular version using boto3 and aws secrets, the version can be used in any platform any condition.

## Instruction
- some parameter need for run.sh also come from config.toml