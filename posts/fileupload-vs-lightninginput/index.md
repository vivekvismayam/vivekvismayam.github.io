# Upload Files In LWC- 𝘭𝘪𝘨𝘩𝘵𝘯𝘪𝘯𝘨-𝘪𝘯𝘱𝘶𝘵 𝘷𝘴 𝘭𝘪𝘨𝘩𝘵𝘯𝘪𝘯𝘨-𝘧𝘪𝘭𝘦-𝘶𝘱𝘭𝘰𝘢𝘥

&nbsp;  


## If you’ve ever handled file uploads in Salesforce LWCs, you’ve probably wondered when to use lightning-input with type="file" versus lightning-file-upload🔍. 

&nbsp;  

Here’s the deal💡:

###  Lightning Input 🚀
**𝘭𝘪𝘨𝘩𝘵𝘯𝘪𝘯𝘨-𝘪𝘯𝘱𝘶𝘵 𝘵𝘺𝘱𝘦="𝘧𝘪𝘭𝘦"**

- 👉Use this when you want to handle files locally (e.g., reading file contents for processing).
- 👉Perfect for things like previewing files or parsing data (think CSVs) and do process in JS with this data rather than saving it in backend.
- 👉An input field for selecting files to upload using an Upload Files button or a drag-and-drop zone. This field accepts files up to 3.5 MB.
- 👉You will need to custom Apex logic in case you need to save the file and remember about 6mb Heap size limit in apex.
- 👉To retrieve the list of selected files, use event.target.files in the onchange event handler. Your selected files are returned in a FileList object, each specified as a File object with the size and type attributes.

Below example allows you to upload an image or Zip file.
```html
<template>
    <lightning-input
        type="file"
        label="Attachment"
        accept="image/png, .zip"
        onchange={handleFilesChange}
        multiple
    >
    </lightning-input>
</template>
```
>lightning-input type="file" handles file selection only. Implement your own file uploading. For example, wire up your component to an Apex controller that handles file uploads. Alternatively, use the lightning-file-upload component for an integrated way to upload files to records.

### Lightning File Upload🚀
**𝘭𝘪𝘨𝘩𝘵𝘯𝘪𝘯𝘨-𝘧𝘪𝘭𝘦-𝘶𝘱𝘭𝘰𝘢𝘥**

- 👉Use this when you need to upload files directly into Salesforce as ContentVersion records.
- 👉It handles files up to 2GB and comes with a built-in progress bar!
- 👉Use onuploadfinished event handler to handle post upload logics in js
- 👉To associate an uploaded file to a record, specify the record-id attribute
 
 Below example creates a file uploader that allows multiple PDF and PNG files to be uploaded.
```html
<template>
    <lightning-file-upload
        label="Upload File"
        name="fileUploader"
        accept={acceptedFormats}
        record-id={myRecordId}
        onuploadfinished={handleUploadFinished}
        multiple
    >
    </lightning-file-upload>
</template>
```
```Js
import { LightningElement, api } from 'lwc';
export default class FileUploadExample extends LightningElement {
    @api
    myRecordId;

    get acceptedFormats() {
        return ['.pdf', '.png'];
    }

    handleUploadFinished(event) {
        // Get the list of uploaded files
        const uploadedFiles = event.detail.files;
        alert('No. of files uploaded : ' + uploadedFiles.length);
    }
}
```

Do add any value points you can think of down in comments!🔦🔦🔦

>Read more 
>-  [Lightning Input](https://developer.salesforce.com/docs/component-library/bundle/lightning-input/documentation) 
>- [Lightning File Upload](https://developer.salesforce.com/docs/component-library/bundle/lightning-file-upload) 


*This Content was originally posted in linkedin [View Post](https://www.linkedin.com/posts/vivekvismayam_%F0%9D%98%AD%F0%9D%98%AA%F0%9D%98%A8%F0%9D%98%A9%F0%9D%98%B5%F0%9D%98%AF%F0%9D%98%AA%F0%9D%98%AF%F0%9D%98%A8-%F0%9D%98%AA%F0%9D%98%AF%F0%9D%98%B1%F0%9D%98%B6%F0%9D%98%B5-%F0%9D%98%B7%F0%9D%98%B4-%F0%9D%98%AD%F0%9D%98%AA%F0%9D%98%A8%F0%9D%98%A9%F0%9D%98%B5%F0%9D%98%AF%F0%9D%98%AA%F0%9D%98%AF%F0%9D%98%A8-%F0%9D%98%A7%F0%9D%98%AA%F0%9D%98%AD%F0%9D%98%A6-%F0%9D%98%B6%F0%9D%98%B1%F0%9D%98%AD%F0%9D%98%B0%F0%9D%98%A2%F0%9D%98%A5-activity-7272587039923957760-qviu?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA_bVqsB5ZA6FQt9Rk3q8WfamtkMsTNLxRo)*

***
