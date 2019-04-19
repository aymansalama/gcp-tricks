# gcp-tricks
This repo to help going through GCP commands and tricks


# Auto mount on fstab
``echo UUID=`sudo blkid -s UUID -o value /dev/sdb` /data ext4 discard,defaults,nofail 0 2 | sudo tee -a /etc/fstab``

# Copy files from external servers to GCP

Make sure you are authenticated and have rights to both projects with the same account!
``$ gcloud config list ``
(if you see the service account @developer.gserviceaccount.com, you need to switch to the account that is enabled on both projects. you can check that from the Devlopers Console > Permissions)
``$ gcloud auth login``
(copy the link to a new window, login, copy the code and paste it back in the prompt)
``$ gcloud compute scp test.tgz --project stack-complete-343 instance-IP:/home/ubuntu --zone us-central1-a ``
(I would also use the instance name instead of the IP)

https://stackoverflow.com/questions/27235349/copy-files-between-two-google-cloud-instances 

# Initiate auth for vm 
``gcloud init``
``gcloud iam service-accounts create anyname``

# Upload files to buckets, please initiate as above with gcloud init first.
``gsutil cp file.csv gs://mybucket``

# GCP mount bucket
``gcsfuse project_name testmount/``
https://cloud.google.com/storage/docs/gcs-fuse
https://github.com/GoogleCloudPlatform/gcsfuse 


# GCP remote host mysql only within the project and configured Network connection. 
``mysql --host=104.197.38.137 --user=root --password``
