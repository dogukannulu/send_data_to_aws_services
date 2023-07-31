# Overview

This process will be running inside an EC2 instance. Therefore, no AWS credential is defined or used inside the scripts. If you want to run locally or somewhere else, you have to add AWS credentials to the scripts.

This part of the repo is created for:

- Check if the Kinesis stream exists or not. If not, create a new stream.
- The CSV file will be retrieved from a URL and will be streaming into the stream with predefined interval and length.
- The CSV won't be modified. If modification is required, you can add to the Python script.
- The script will be valid for the region `eu-central-1`, but you can modify the region part if necessary.

## Steps

1. First, we have to run this command to bring the `setup.sh` into the EC2 instance (We have to be located in `/`).
```
sudo curl -O https://raw.githubusercontent.com/dogukannulu/send_data_to_aws_services/csv_to_kinesis_refactor/csv_to_kinesis_streams/setup.sh
```

2. The shell script runs the Python script with predefined command line arguments. You can modify lines 51-55 in `setup.sh` according to your use case. To modify or execute the shell script we should run the following command.
```
sudo chmod u+rwx setup.sh
```

3. After modifications (if necessary), we can create the working directory `/project` and execute the shell script.
```
sudo mkdir project
sudo ./setup.sh
```

## Notes

- All the processes will be running in `/project` directory after executing `setup.sh`
- You can see all the logs in `/project/csv_to_kinesis_streams.log` 
- zip file includes `csv_to_kinesis_streams.py` and `requirements.txt`
- Shell script will download necessary packages, libraries first. Then, will install requirements and run the Python script
