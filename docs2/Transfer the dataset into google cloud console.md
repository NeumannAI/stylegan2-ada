# Transfer The Dataset Into Google Cloud Console

This markdown document demonstrate how to use the Google Cloud Console to create Cloud Storage buckets, 
load the dataset into a storage bucket, and load it into the Juypter Notebook on the Google Cloud.

## Before you begin
Make sure that:
-  You have the the gcloud CLI installed into your local, if not follow the installation instruction [here](https://cloud.google.com/sdk/docs/install) 
- You set the working project that you want to upload your data into it. To set the project property in the core section, run: 
```
gcloud config set project PROJECT_ID
```
### Steps

- Create storage buckets
- Transfer the data from your local storage into Google console. 
- Load it into the Juypter Notebook on the Google Cloud


### 1- Create storage buckets

In the Google Cloud Console:
- Go to the Cloud Storage Browser page from the menu on the left side of the console.
- Click Create bucket.
- On the Create a bucket page, enter your bucket information. To go to the next step, click Continue. 
- Click Create. 

> Note:Bucket names must be globally unique (among all buckets ever created by any user).

### 2- Transfer the data from your local storage into Google console. 

To transfer the data using the multi-parallel data transfer, run: 
```gsutil -m cp -r [dataset path] gs://[bucket name]```

### 3- Load it into the Juypter Notebook on the Google Cloud
The dataet stored on the storage bucket, run this command in the JupyterLab terminal and the data will be loaded into the JupyterLab.
```
gsutil -m cp -r gs://[bucket ID] . Or gsutil -m cp -r dir gs://[bucket ID / Folder name] .
```

