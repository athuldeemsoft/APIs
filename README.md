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
        
- Upload files (.xml) for annotation.
    - POST: /Annotations/upload/:image_unique_id/:file_type
      
            **Response**
            ```
            {
                status: 'Done'
            }
            ```
            
      *Send file as 'upload_file'
            
- User Directory Tree
    
    - GET: /Users/treeinfo/:id
        
        Default (initial) response data will look like below, this will be the root directory. When creating initial folders the parent value need to be the same as the id of its parent/outer folder (directory). The children array will contain the id of all the children a folder have. 
        
        **Response**
        ```
        [
          {
            "id": "root",
            "name": "root",
            "type": "folder",
            "parent": "None",
            "children": [],
            "props": {}
          }
        ]
        ```
        
    - POST: /Users/treeinfo/:id
        
        When creating a folder/file the request should contain these values.
    
        **Request**
        ```
        {
          "name": "folder/file name",
          "type": "folder/file",
          "parent": "parent folder id",
          "children": [],
          "props": {}
        }
        ```
        
        *All fields are necessary, the response will be the updated array.
        
    - PUT: /Users/treeinfo/:id
        
        User can alter the name/props of folder/file, the request should contain these values.
        
        **Request**
        ```
        {
          "name": "folder/file name",
          "type": "folder/file",
          "parent": "parent folder id",
          "children": [],
          "props": {},
          "id" : "folder id"
        }
        ```
        
        *Only id, name and props fields are necessary, the response will be the updated array.
        
    - DELETE: /Users/treeinfo/:id
        
        The request should have these values
        
        **Request**
         ```
        {
          "name": "folder/file name",
          "type": "folder/file",
          "parent": "parent folder id",
          "children": [],
          "props": {},
          "id" : "folder id"
        }
        ```
        
        *Only id and parent fields are necessary.
  
    
- Get Tissue area, Cancer volume and Gleason grade values of image.
    - GET: /Images/metric/:id
   
    *This data will be generated only after user edits the annotation. The response will be a JSON object that converted to string. This data will also be present in the response when saving annotation.
        
