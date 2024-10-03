Image upload using presigned url

![[aws-s3-file-upload.excalidraw]]


**Task: Implement Image Upload using Presigned URLs in AWS S3**

1. **Set Up AWS S3 Bucket**
   - [x] Create an S3 bucket for product images.
   - [x] Configure bucket permissions to allow secure uploads.
   - [ ] (Optional) Set up public access policies or versioning.

2. **Configure AWS in Backend**
	- [x] Install AWS SDK in Node.js backend.
   - [x] Set environment variables for AWS credentials (access key, secret key, region).
   - [x] Initialize AWS S3 service in the backend.

3. **Create API Endpoint for Presigned URL**
   - [x] Create an API route to generate presigned URLs.
   - [x] Implement logic for generating presigned URLs with expiration time.

4. **Request Presigned URL in Frontend**
   - [ ] Modify frontend to request presigned URL from backend before uploading images.
   - [ ] Pass file name and type to backend for URL generation.

5. **Upload Image to S3**
   - [ ] Implement file upload to S3 using the presigned URL in the frontend.
   - [ ] Handle success and error responses from S3.

6. **Store Image URL in Database**
   - [ ] Save the S3 image URL in PostgreSQL for the corresponding product.

7. **Testing and Validation**
   - [ ] Test upload flow with various file sizes and types.
   - [ ] Handle failure cases (e.g., expired URL, incorrect permissions).

**My flow:**

single page form where I need to upload product info and image at the same time
1. send the json back to addProduct controller in the backend which add the product to the backend
2. putObjectAws middleware to handle the addProduct to upload image to aws s3
3. and send back presigned url to frontend which complete the upload process, within the same call
4. and later getSignedUrl as after puting the object in s3 to return to backend and finalize the addProduct operation using the same route
I am planning to do this as a single route operation where within it, the call to s3 is done. I don't know if this is a sound idea. 

For **multiple image uploads**, the recommended flow can still work but requires some adjustments to handle the upload of several images simultaneously without affecting the user experience.

**recommended flow by chat gpt**

1. **Single Form UI with Multiple Image Upload Section**:
   - The user still sees one unified form with both the image upload section and product info fields.
   - In the **image upload section**, allow the user to select **multiple images** at once.
   - Display each selected image as a thumbnail with a progress bar or loading indicator next to it as they are uploaded individually to S3.

2. **Behind the Scenes: Asynchronous Multiple Image Uploads**:
   - For each image the user selects, you **immediately request a presigned URL** from the backend.
   - Upload each image to S3 **in parallel** using their respective presigned URLs. This can be done asynchronously in the background while the user fills out the rest of the form.
   - Store the S3 URLs of the successfully uploaded images in hidden form fields to be submitted later with the product info.

3. **Frontend Process for Multiple Image Upload**:
   - As the user selects multiple images, start uploading them concurrently.
   - **Display a progress bar for each image** so the user can track the upload status.
   - After each image is uploaded, display a success message or mark the upload as complete. If an image fails to upload, notify the user so they can retry that specific image.

4. **Submit Product Info with All Image URLs**:
   - Once the images are uploaded and the product info is filled out, the user submits the form.
   - All S3 URLs (from the uploaded images) are sent along with the product info in a single request to the backend.

#### Considerations for Multiple Image Upload:
1. **Async Handling in Frontend**:
   - Ensure that each image upload runs in parallel without blocking other operations in the form.
   - Use a state management solution (e.g., React state or context) to keep track of which images have been uploaded successfully and which ones have failed.

2. **Backend Handling**:
   - The backend generates presigned URLs for **multiple images** when requested.
   - Ensure the database schema is flexible enough to store multiple image URLs associated with one product.

3. **Error Handling**:
   - Handle upload errors for individual images gracefully. Allow users to retry uploading any failed image without affecting the entire form submission.
   - If some images fail to upload, ensure that form submission is disabled or appropriately flagged until all images have been uploaded successfully.

#### Is This Feasible for Multiple Image Upload?
Yes, this flow is feasible even for multiple image uploads. Here’s why:
- **Parallel Uploads**: Using presigned URLs allows you to upload each image asynchronously without overloading the server.
- **Frontend Flexibility**: The UI can show the progress for each image separately, so users have a clear idea of what’s happening with each file.
- **Scalability**: This approach scales well, even if the user uploads many images at once, as the S3 upload process happens independently for each file.

The key challenge here is making sure that the UI stays responsive and that you handle errors for each image independently. But overall, this flow should work smoothly even with multiple image uploads.