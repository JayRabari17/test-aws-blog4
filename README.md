import boto3

def main():
    ec2 = boto3.client('ec2')
    regions = [region['RegionName'] 
               for region in ec2.describe_regions()['Regions']]
    
    for region in regions:
        print(f"Instances in {region}:")
        ec2 = boto3.client('ec2', region_name=region)
        instances = ec2.describe_instances()
        for reservation in instances["Reservations"]:
            for instance in reservation["Instances"]:
                print(instance["InstanceId"])

if __name__ == "__main__":
    main()