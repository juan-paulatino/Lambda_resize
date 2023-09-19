# Lambda_resize
![Screen Shot 2023-09-18 at 22 39 12](https://github.com/juan-paulatino/Lambda_resize/assets/118320209/1ac30969-a70c-4957-8403-3b256f948077)


This Python script is designed to be used as an AWS Lambda function. It listens for S3 bucket events and automatically resizes images that are uploaded to the bucket. Here’s a brief explanation of the code:

Imports: The script imports several libraries, including boto3 (the AWS SDK for Python), os and sys (for interacting with the operating system), uuid (for generating unique identifiers), urllib.parse (for URL manipulation), and PIL.Image (Python Imaging Library for image processing).

S3 Client: An S3 client is created using boto3.client('s3'). This client is used to interact with the S3 service.

resize_image Function: This function takes an image path and a resized path as input. It opens the image, resizes it to half its original size using the thumbnail method, and then saves the resized image to the resized path.

lambda_handler Function: This is the main function that AWS Lambda calls when the script is executed. It takes an event object and a context object as input.

The function starts by printing a message to indicate that image resizing has begun.
It then loops over each record in the event object. Each record represents an S3 event.
For each record, it extracts the bucket name and object key from the event data.
It then creates temporary paths for downloading and uploading images.
The original image is downloaded from S3 to a temporary location, resized using the resize_image function, and then uploaded back to a different S3 bucket.
Finally, it prints a message indicating that image resizing is complete.
This script is typically used in scenarios where you want to automatically resize images that are uploaded to an S3 bucket, perhaps to create thumbnails or reduce storage costs. The resized images are stored in a separate S3 bucket specified by the RESIZED_BUCKET environment variable.
