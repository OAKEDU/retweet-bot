Python Retweet Bot
==================

![alt text](https://img.shields.io/badge/python-3.5-green.svg "Python3.5")

Forked from this project: https://github.com/basti2342/retweet-bot

- This script retweets all Tweets containing your search term. 
- Optionally, you can restrict retweets to people you follow
- Optionally, you can automatically follow users that use your search term
- A savepoint file is created each time the script is run so it can pick up where it left off the previous time it was run.
- Twitter API v1.1 ready. 

Setup:
-------------
- copy `sample-config` and rename to `config`
- fill out the config file for your project (more info in the file)

### Running Locally
This project is meant to run as an AWS Lambda function and leverages a project called [python-lambda](https://github.com/nficano/python-lambda) to assist with the testing and deployment.

Dependencies:
1. pyenv (install via homebrew, add to path)
2. pyenv-virtualenv (install via homebrew, add to path)
3. create a virtualenv called retweet

4. pip install requirements
5. `lambda invoke`

Some details / links: #7

### Deploying
6. Create a user in AWS if you don't have one and [put credentials in `.aws/credentials` config file](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)
7. Create a role with basic Lambda policy and put the name of it in the `role:` attr in `config.yaml` (I needed to put `service-role/` prefix in front of name.
8. `lambda deploy`

### Known Issues

#### Savepoint
Lambdas don't have storage and I didn't set up an s3 bucket yet. Right now it writes a savepoint to `/tmp` which is transient Lambda storage. You may need to clear the file locally to debug.
