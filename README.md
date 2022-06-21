# API List
- Users & Images list.
    - GET: /Users/imagelist
        - Res
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
    - GET: /Images/userid/<int:user_id>
        - Res
        ```
        [<image_object>,...]
        ```

- Start/Stop image prediction.
    - GET: /Images/predict/<string:image_unique_id>
        - Res
        ```
        {
            success: "__", 
            status: "__"
        }
        ```

- Log info list.
    - GET: /LogInfo
    - GET: /LogInfo/<string:image_unique_id>
        - Res
        ```
        [<log_object>,...]
        ```

- Add/Remove userid from images.
    - POST: /Images/adduser/
    - POST: /Images/removeuser/
        - Req
        ```
        {
            userid: <id>,
            imageid: <image_unique_id>
        }
        ```

        - Res
        ```
        {
            success: "__",
            msg: "__",
            users: [<id>,...]
        }
        ```
