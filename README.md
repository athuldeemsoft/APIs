# PathomIQ API List
- Users & Images list.
    - GET: /Users/imagelist
        
        **Response**
        ```
        [
            {
                userid: <id>,
                images: [<image_object>,...]
            },
            ...
        ]
        ```

- Image list by user id.
    - GET: /Images/userid/:id
        
        **Response**
        ```
        [<image_object>,...]
        ```

- Start image prediction.
    - GET: /Images/startpredict/:image_unique_id
        
        **Response**
        ```
        {
            success: __, 
            status: "__",
            image: <object>
        }
        ```
- Stop image prediction.
    - GET: /Images/stoppredict/:image_unique_id
        
        **Response**
        ```
        {
            success: __, 
            status: "__",
            image: <object>
        }
        ```

- Log info list.
    - GET: /LogInfo
    - GET: /LogInfo/:image_unique_id
        
        **Response**
        ```
        [<log_object>,...]
        ```

- Add/Remove/Update userid to image's Shared column.
    - POST: /Images/adduser
    - POST: /Images/removeuser
    - POST: /Images/updateuser
        
        **Request**
        ```
        {
            userid: [<int:id>,<int:id>,...],
            imageid: <image_unique_id>
        }
        ```

        **Response**
        ```
        {
            success: __,
            status: "__",
            image: <object>
        }
        ```
- Delete image.
    - DELETE: /Images/:image_unique_id
        
        **Response**
        ```
        {
            success: __,
            status: "__"
        }
        ```
        
- Add log.
    - POST: /LogInfo
    
        **Request**
        ```
        {
            imageid:"8639e81f98bd42f7b29fa2efabebbaf3",
            type: "Tiling",
            message: "Tiling is running"
        }
        ```
        
        **Response**
        ```
        {
            success: True/False,
            msg: "___"
        }
        ```
                  
- Image upload/download operations.
    - Add image data into database table, POST: /Images         
    
        **Request**
        ```
        {
          "patient_id": 1,
          "entity_id": 4,
          "filename": "Test.png",
          "userid": 19,
          "workarea": 6,
          "study": 5
        }
        ```
        
        **Response**
        ```
        {
          "id": 78,
          "image_unique_id": "d3171c32ce9448f387319b4e1dc6d292",
          "workarea_id": null,
          "entity_id": "4",
          "study_id": null,
          "patient_id": "1",
          "filename": "Test.png",
          "location": null,
          "description": null,
          "workarea": null,
          "study": null,
          "adddate": "2022-08-17 06:59:27.530508",
          "moddate": "2022-08-17 06:59:27.530508",
          "status": "In Progress",
          "base_download_url": null,
          "base_raw_download_url": null,
          "tissue_area": null,
          "outcome_prediction": null,
          "shared": "19",
          "annotation_status": "Pending",
          "tissuearea_status": "Pending",
          "tiling_status": "Pending",
          "metric": null,
          "response": {
            "url": "https://pathomiq-dev.s3.amazonaws.com/",
            "key": "d3171c32ce9448f387319b4e1dc6d292",
            "AWSAccessKeyId": "AKIA3EZURXYHVJR7DR7X",
            "policy": "eyJleHBpcmF0aW9uIjogIjIwMjItMDgtMTdUMDc6NTk6MjdaIiwgImNvbmRpdGlvbnMiOiBbeyJidWNrZXQiOiAicGF0aG9taXEtZGV2In0sIHsia2V5IjogImQzMTcxYzMyY2U5NDQ4ZjM4NzMxOWI0ZTFkYzZkMjkyIn1dfQ==",
            "signature": "FKbPpy54hLCU8cQ/M75XXmWnE2c="
          }
        }
        ```
        
    - Upload file to AWS, use the response.url from the POST: /Images response data as the AWS url and request a POST method.

            **Request**
            ```
            {
                file: file,
                AWSAccessKeyId: <>,
                key: <>,
                policy: <>,
                signature: <>,
                upload_file: 'true'
            }
            ```
      
    - Update image data in the database table, PUT: /Images/<int:id>         
    
        **Request**
         ```
        {
          "status": "Uploaded",
          "entity_id": 4,
          "patient_id": 3,
          "location": "dddddddddddddd",
          "workarea_id": 6,
          "description": "xxxxxxxx"
          "study_id": 5
        }
        ```
        *All fileds are not necessary, only the ones are required is enough.
        
    - Download image file, GET: S3/file/<image_unique_id>
            
- Upload and Download XML files.
    -  Upload XML for annotation, POST: /Annotations/upload
           
          **Request**
            ```
           {
                "upload_file": file,
                "imageid": 548,
                "userid": 19,
                "fileid": <image_unique_id>
            }
            ```
            
     - To download the XML use the *base_raw_download_url* value from the image data. Eg: <image.base_raw_download_url>/<image.image_unique_id>_complete_net_prediction.xml
            
