# API List
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
        
