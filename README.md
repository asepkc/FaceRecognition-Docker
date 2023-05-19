<p align="left">
  <img src="https://user-images.githubusercontent.com/125717930/225975240-24b9a8ad-8cc6-4d5f-9a91-1435951b0bd7.png" width="120" alt="Nest Logo" />
</p>

👏  We have published the Face Livness Detection SDK for the server.

  - [FaceLivenessDetection-Docker](https://github.com/kby-ai/FaceLivenessDetection-Docker)

# FaceRecognition-Docker

This project demonstrates an advanced face recognition technology implemented via a Dockerized Flask API.

It includes features that allow for testing face recognition between two images using both image files and base64-encoded images.

> The demo is integrated with KBY-AI's Face Recognition Server SDK.

> We can customize the SDK to align with your specific requirements.

  | Face Liveness Detection      | Face Recognition |
  |------------------|------------------|
  | Face Detection        | Face Detection    |
  | Face Liveness Detection        | Face Recognition    |
  | Pose Estimation        | Pose Estimation    |
  | 68 points Face Landmark Detection        | 68 points Face Landmark Detection    |
  | Face Quality Calculation        | Face Occlusion Detection        |
  | Face Occlusion Detection        | Face Occlusion Detection        |
  | Eye Closure Detection        | Eye Closure Detection       |
  | Mouth Opening Check        | Mouth Opening Check        |

> Reference
> - [Face Liveness Detection - Android(Basic SDK)](https://github.com/kby-ai/FaceLivenessDetection-Android)
> - [Face Liveness Detection - iOS(Basic SDK)](https://github.com/kby-ai/FaceLivenessDetection-iOS)
> - [Face Recognition - Android(Stdndard SDK)](https://github.com/kby-ai/FaceRecognition-Android)
> - [Face Recognition - iOS(Stdndard SDK)](https://github.com/kby-ai/FaceRecognition-iOS)
> - [Face Attribute - Android(Premium SDK)](https://github.com/kby-ai/FaceAttribute-Android)
> - [Face Attribute - iOS(Premium SDK)](https://github.com/kby-ai/FaceAttribute-iOS)

## Try the API
### Website
  You can test the SDK using images from the following URL:
  http://18.221.33.238:9000/
  
### Postman
  To test the API, you can use Postman. Here are the endpoints for testing:
  - Test with an image file: Send a POST request to http://18.221.33.238:8081/compare_face
  - Test with a base64-encoded image: Send a POST request to http://18.221.33.238:8081/compare_face_base64

    You can download the Postman collection to easily access and use these endpoints. [click here](https://github.com/kby-ai/FaceRecognition-Docker/tree/main/postman/kby-ai-face.postman_collection.json)
    
    ![image](https://github.com/kby-ai/FaceRecognition-Docker/assets/125717930/dce48454-6d41-46f0-9623-b26bec103616)


## SDK License

This project uses KBY-AI's Face Recognition Server SDK, which requires a license per machine.

- The code below shows how to use the license: https://github.com/kby-ai/FaceRecognition-Docker/blob/5c6bdaff0e8154d6c6472ac9faf9158c6a6e7b47/app.py#L26-L36

- In order to request the license, please provide us with the machine code obtained from the "getMachineCode" function.

  Please contact us:
  ```
  Email: contact@kby-ai.com

  Telegram: @kbyai

  WhatsApp: +19092802609

  Skype: live:.cid.66e2522354b1049b
  
## How to run

### 1. System Requirements
  - CPU: 2 cores or more (Recommended: 2 cores)
  - RAM: 4 GB or more (Recommended: 8 GB)
  - HDD: 4 GB or more (Recommended: 8 GB)
  - OS: Ubuntu 20.04 or later
  - Dependency: OpenVINO™ Runtime (Version: 2022.3)

### 2. Setup and Test
  - Clone the project:
    ```
    https://github.com/kby-ai/FaceRecognition-Docker.git
    ```
  - Download the model from Google Drive: [click here](https://drive.google.com/file/d/19vA7ZOlo19BcW8v4iCoCGahUEbgKCo48/view?usp=sharing)
    ```
    cd FaceLivenessDetection-Docker
    
    wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=19vA7ZOlo19BcW8v4iCoCGahUEbgKCo48' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=19vA7ZOlo19BcW8v4iCoCGahUEbgKCo48" -O data.zip && rm -rf /tmp/cookies.txt
    
    unzip data.zip
    ```
  - Build the Docker image:
    ```
    sudo docker build --pull --rm -f Dockerfile -t kby-ai-face:latest .
    ```
  - Run the Docker container:
    ```
    sudo docker run -v ./license.txt:/home/openvino/kby-ai-face/license.txt -p 8081:8080 kby-ai-face
    ```
  - Send us the machine code and replace the license.txt file you received. Then, run the Docker container again.
    
    ![image](https://github.com/kby-ai/FaceLivenessDetection-Docker/assets/125717930/216f1306-a758-4e47-a8fe-159f3c84f53b)
    
    ![image](https://github.com/kby-ai/FaceLivenessDetection-Docker/assets/125717930/2eff3496-abc2-4e70-bee1-4195375f42e6)


  - To test the API, you can use Postman. Here are the endpoints for testing:

    Test with an image file: Send a POST request to http://{xx.xx.xx.xx}:8081/compare_face
    
    Test with a base64-encoded image: Send a POST request to http://{xx.xx.xx.xx}:8080/compare_face_base64
    
    You can download the Postman collection to easily access and use these endpoints. [click here](https://github.com/kby-ai/FaceRecognition-Docker/tree/main/postman/kby-ai-face.postman_collection.json)


## About SDK

### 1. Initializing the SDK

- Step One

  First, obtain the machine code for activation and request a license based on the machine code.
  ```
  machineCode = getMachineCode()
  print("machineCode: ", machineCode.decode('utf-8'))
  ```
  
- Step Two

  Next, activate the SDK using the received license.
  ```
  setActivation(license.encode('utf-8'))
  ```  
  If activation is successful, the return value will be SDK_SUCCESS. Otherwise, an error value will be returned.

- Step Three

  After activation, call the initialization function of the SDK.
  ```
  initSDK("data".encode('utf-8'))
  ```
  The first parameter is the path to the model.

  If initialization is successful, the return value will be SDK_SUCCESS. Otherwise, an error value will be returned.

### 2. Enum and Structure
  - SDK_ERROR
  
    This enumeration represents the return value of the 'initSDK' and 'setActivation' functions.

    | Feature| Value | Name |
    |------------------|------------------|------------------|
    | Successful activation or initialization        | 0    | SDK_SUCCESS |
    | License key error        | -1    | SDK_LICENSE_KEY_ERROR |
    | AppID error (Not used in Server SDK)       | -2    | SDK_LICENSE_APPID_ERROR |
    | License expiration        | -3    | SDK_LICENSE_EXPIRED |
    | Not activated      | -4    | SDK_NO_ACTIVATED |
    | Failed to initialize SDK       | -5    | SDK_INIT_ERROR |

- FaceBox
  
    This structure represents the output of the face detection function.

    | Feature| Type | Name |
    |------------------|------------------|------------------|
    | Face rectangle        | int    | x1, y1, x2, y2 |
    | Face angles (-45 ~ 45)        | float    | yaw, roll, pitch |
    | Face quality (0 ~ 1)        | float    | face_quality |
    | Face luminance (0 ~ 255)       | float    | face_luminance |
    | Eye distance (pixels)       | float    | eye_dist |
    | Eye closure (0 ~ 1)       | float    | left_eye_closed, right_eye_closed |
    | Face occlusion (0 ~ 1)       | float    | face_occlusion |
    | Mouth opening (0 ~ 1)       | float    | mouth_opened |
    | 68 points facial landmark        | float [68 * 2]    | landmarks_68 |
    | Face templates        | unsigned char [2048]    | templates |
  
    > 68 points facial landmark
    
    <img src="https://user-images.githubusercontent.com/125717930/235560305-ee1b6a39-5dab-4832-a214-732c379cabfd.png" width=500/>

### 3. APIs
  - Face Detection
  
    The Face SDK provides a single API for detecting faces, determining face orientation (yaw, roll, pitch), assessing face quality, detecting facial occlusion, eye closure, mouth opening, and identifying facial landmarks.
    
    The function can be used as follows:

    ```
    faceBoxes = (FaceBox * maxFaceCount)()
    faceCount = faceDetection(image_np, image_np.shape[1], image_np.shape[0], faceBoxes, maxFaceCount)
    ```
    
    This function requires 5 parameters.
    * The first parameter: the byte array of the RGB image buffer.
    * The second parameter: the width of the image.
    * The third parameter: the height of the image.
    * The fourth parameter: the 'FaceBox' array allocated with 'maxFaceCount' for storing the detected faces.
    * The fifth parameter: the count allocated for the maximum 'FaceBox' objects.

    The function returns the count of the detected face.