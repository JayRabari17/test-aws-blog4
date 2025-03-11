import boto3

def main():
    ec2 = boto3.client('ec2')
    instances = ec2.describe_instances()
    for reservation in instances["Reservations"]:
        for instance in reservation["Instances"]:
            print(instance["InstanceId"])

if __name__ == "__main__":
    main()