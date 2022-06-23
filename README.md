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

- Start/Stop image prediction.
    - GET: /Images/predict/:image_unique_id
        Response
        ```
        {
            success: __, 
            status: "__"
        }
        ```

- Log info list.
    - GET: /LogInfo
    - GET: /LogInfo/:image_unique_id
        
        **Response**
        ```
        [<log_object>,...]
        ```

- Add/Remove userid from images.
    - POST: /Images/adduser/
    - POST: /Images/removeuser/
        
        **Request**
        ```
        {
            userid: <id>,
            imageid: <image_unique_id>
        }
        ```

        **Response**
        ```
        {
            success: __,
            msg: "__",
            users: [<id>,...]
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
