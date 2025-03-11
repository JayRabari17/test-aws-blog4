import boto3

def main():
    s3 = boto3.client('s3')
    bucket_name = 'my-bucket'
    object_key = 'folder/file.txt'
    s3.download_file(bucket_name, object_key, 'downloaded-file.txt')

if __name__ == '__main__':
    main()