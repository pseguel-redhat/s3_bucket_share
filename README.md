# Create an S3 Bucket for sharing

My use case is using S3 for sharing files 
with a third party. This Ansible playbook 
automates the bucket setup. 

This playbook:
- creates a S3 bucket
- creates an user and an access key
- configures a policy for this user

Then the third party can use a tool such as Cyberduck 
for uploading the file.

## Usage:
 
```
ansible-playbook create_public_bucket.yml -e @extra_vars.yaml
```

Via the file `extra_vars.yml` you can customize:
- user name via variable `user_name`
- bucket name via variable `bucket_name`

Use `extra_vars.yml.example` as an example. 

This playbooks assumes you have AWS credentials set 
in these env vars:
- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_REGION`

There's an `aws.env.example` file you can use with `source aws.env.example`.  

After running the playbook you´ll get a bucket address
and access key you can share with whoever needs to share
files with you.


## Delete user and bucket

Just execute the following:
```
ansible-playbook delete_public_bucket.yml -e @extra_vars.yaml
```
