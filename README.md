### 미니 프로젝트: 실시간 카메라 명함 정보 추출 시스템

본 문서는 실시간 카메라 명함 정보 추출 미니 프로젝트에 대한 개요, 사용 방법, 주요 기능 및 개발 과정에서 고려되었던 사항들을 설명합니다 

## 1.프로젝트 개요

본 프로젝트는 OpenVINO를 활용한 텍스트 감지 모델과 Tesseract OCR엔진을 이용하여  실시간 카메라 영상에서 명함 정보를 추출하고, 추출된 정보(이름,전화번호,이메일 등)을 저장하는 시스템입니다.
명함 이미지에서 텍스트 영역을 찾아내고, 광학 문자 인식(OCR)을 통해 텍스트를 추출하여 효율적인 정보 관리 및 활용을 목표로 합니다.

## 2.Skill & Tool


* Python:

* OpenCV: 카메라 스트림 처리 및 이미지 조작에 사용

* OpenVINO: 텍스트 감지 모델을 실행 및 최적화를 위한 Intel 툴킷킷

* PyTesseract: 이미지에서 텍스트를 추출하기 위한 OCR라이브러리

* horizontial-text-detection-0001: OpenVINO 수평 텍스트 감지모델


## 3.시스템 구성

1.  **웹 카메라 입력:** 실시간으로 명함 이미지를 캡처합니다<sup>3</sup>.
2.  **OpenVINO 텍스트 감지** 캡쳐 이미지에서 텍스트 영역 감지<sup>3</sup>.

## 4.설치 및 실행방법

1.  **필수 라이브러리 설치:**
    ```bash
    pip install opencv-python numpy pytesseract openvino-dev
    ```
2.  **Tesseract OCR 엔진 설치:** Tesseract OCR 엔진을 별도로 설치해야 합니다. 운영체제에 맞는 설치 방법을 검색하여 설치하십시오. 또한, Python에서 Tesseract를 사용하기 위해 Tesseract 실행 파일의 경로를 `pytesseract`에 설정해야 할 수도 있습니다.
3.  **OpenVINO 모델 다운로드 확인:** 프로젝트 실행 시 `horizontal-text-detection-0001` 모델이 `./hellow-detection/model` 디렉토리에 존재하는지 확인합니다<sup>1</sup>.... 모델이 없다면 다운로드해야 한다는 메시지가 출력되고 프로그램이 종료됩니다<sup>8</sup>. OpenVINO Model Downloader 또는 브라우저를 통해 직접 다운로드하여 해당 경로에 저장할 수 있습니다.
4.  **실행:**
    ```bash
    python your_main_script.py  # 실제 실행 파일명으로 변경
    ```
5.  **사용 방법:**
    * 웹캠이 활성화되면 카메라 화면이 표시됩니다<sup>6</sup>....
    * `c` 키를 누르면 현재 카메라 화면을 캡처하여 텍스트 감지 및 정보 추출 과정을 수행합니다<sup>9</sup>.
    * 처리된 이미지 (텍스트 영역이 표시된 이미지)는 `./hellow-detection/output_detected_image_from_camera.jpg` 파일로 저장됩니다<sup>10</sup>.
    * 추출된 텍스트 목록은 `./hellow-detection/extracted_text.txt` 파일로 저장됩니다<sup>10</sup>.
    * 추출된 이름, 전화번호, 이메일 정보는 `./hellow-detection/extracted_info.txt` 파일로 저장됩니다<sup>7</sup>. 전화번호는 '-' 구분자로 연결되어 저장됩니다<sup>11</sup>.
    * 처리된 결과 이미지가 화면에 표시됩니다<sup>7</sup>.
    * `q` 키를 누르면 프로그램을 종료합니다<sup>12</sup>.

## 5.주요기능

1.  **필수 라이브러리 설치:**
    ```bash
    pip install opencv-python numpy pytesseract openvino-dev
    ```
2.  **Tesseract OCR 엔진 설치:** Tesseract OCR 엔진을 별도로 설치해야 합니다. 운영체제에 맞는 설치 방법을 검색하여 설치하십시오. 또한, Python에서 Tesseract를 사용하기 위해 Tesseract 실행 파일의 경로를 `pytesseract`에 설정해야 할 수도 있습니다.
3.  **OpenVINO 모델 다운로드 확인:** 프로젝트 실행 시 `horizontal-text-detection-0001` 모델이 `./hellow-detection/model` 디렉토리에 존재하는지 확인합니다<sup>1</sup>.... 모델이 없다면 다운로드해야 한다는 메시지가 출력되고 프로그램이 종료됩니다<sup>8</sup>. OpenVINO Model Downloader 또는 브라우저를 통해 직접 다운로드하여 해당 경로에 저장할 수 있습니다.
4.  **실행:**
    ```bash
    python your_main_script.py  # 실제 실행 파일명으로 변경
    ```
5.  **사용 방법:**
    * 웹캠이 활성화되면 카메라 화면이 표시됩니다<sup>6</sup>....
    * `c` 키를 누르면 현재 카메라 화면을 캡처하여 텍스트 감지 및 정보 추출 과정을 수행합니다<sup>9</sup>.
    * 처리된 이미지 (텍스트 영역이 표시된 이미지)는 `./hellow-detection/output_detected_image_from_camera.jpg` 파일로 저장됩니다<sup>10</sup>.
    * 추출된 텍스트 목록은 `./hellow-detection/extracted_text.txt` 파일로 저장됩니다<sup>10</sup>.
    * 추출된 이름, 전화번호, 이메일 정보는 `./hellow-detection/extracted_info.txt` 파일로 저장됩니다<sup>7</sup>. 전화번호는 '-' 구분자로 연결되어 저장됩니다<sup>11</sup>.
    * 처리된 결과 이미지가 화면에 표시됩니다<sup>7</sup>.
    * `q` 키를 누르면 프로그램을 종료합니다<sup>12</sup>.

## 6.고려 사항 및 개선점 

* **흑백 이미지 처리:** 흑백으로 변환된 이미지에서 텍스트 인식률이 저하되는 현상이 있었습니다<sup>13</sup>. 이미지 전처리 과정 개선을 통해 이 문제를 완화할 수 있습니다<sup>13</sup>.
* **이름 인식 정확도 향상:** 단순히 성씨로 시작하는 단어를 이름으로 인식하기 때문에, 성씨가 아닌 단어가 이름으로 잘못 인식될 수 있습니다<sup>6</sup>.... 데이터베이스 확충 및 자연어 처리 기술을 도입하여 이름 인식 정확도를 높일 수 있습니다<sup>13</sup>.
* **외부 환경 요인:** 빛, 카메라 각도, 흔들림 등 외부 환경 요인에 따라 텍스트 감지 및 인식 성능이 저하될 수 있습니다<sup>13</sup>. 안정적인 촬영 환경을 안내하고, 이미지 품질 향상 기술을 추가적으로 적용하도록 하겠습니다<sup>13</sup>.