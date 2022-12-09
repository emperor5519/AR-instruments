# AR-instruments
카메라 화면을 통해 AR 가상 악기를 연주해 볼 수 있는 프로젝트 입니다.  
C++ 언어로 작성하였고 OpenCV 라이브러리를 이용해 영상처리를 하였습니다.  
가상의 피아노와 드럼을 연주할 수 있으며 피아노 선택 시 손가락, 드럼 선택 시 빨간색과 파란색 물체를 이용해 연주할 수 있습니다.  
### 

# 블럭도
<img src="/img/블럭도.png" width="400" height="300">  

### 

# 기능 설명
## 1. 영상 변환기능 ##  
<img src="/img/영상변환기능.png" width="400" height="300">  

- 카메라 화면의 RGB영상을 HSV영상 또는 YCrCb영상으로 변환합니다.

```c++
// RGB 영상을 HSV 영상 또는 YCrCb 영상으로 변환
cvtColor(frame, frame_hsv, COLOR_BGR2HSV); // 드럼 선택 상태시
cvtColor(frame, frame_YCrCb, COLOR_BGR2YCrCb); // 피아노 선택 상태시
```

### 

## 2. 손 색상 영역 이진화 기능 ##  
<img src="/img/영상이진화.png" width="400" height="300">  

- 변환된 YCrCb영상에서 손 피부색 영역에 해당하는 범위의 값을 추출해 이진화 합니다.

```c++
// YCrCb 영상의 특정 범위(손 피부색 영역)의 두 임계값 사이의의 값만 추출
inRange(frame_YCrCb, Scalar(0, 133, 77), Scalar(255, 173, 127), frame_bin);
```

### 

## 3. 손가락 끝 검출기능##  
<img src="/img/손가락끝검출.png" width="400" height="300">  

- 최초 실행시 원하는 악기를 선택할 수 있고, 선택 이후에도 화면의 우측 상단의 메뉴를 통해 악기 변경이 가능합니다.

### 

## 3. 무게중심 검출기능 ##  
<img src="/img/선택화면.png" width="400" height="300">  

- 최초 실행시 원하는 악기를 선택할 수 있고, 선택 이후에도 화면의 우측 상단의 메뉴를 통해 악기 변경이 가능합니다.

### 

## 4. 악기 선택기능 ##  
<img src="/img/연주.png" width="600" height="300">

- 드럼스틱 또는 손가락 끝 좌표를 이용해 카메라 화면상의 악기 영역 안으로 움직이면 악기의 소리가 재생됩니다.

### 

## 5. 소리 출력기능 ##  
<img src="/img/연주.png" width="600" height="300">

- 드럼스틱 또는 손가락 끝 좌표를 이용해 카메라 화면상의 악기 영역 안으로 움직이면 악기의 소리가 재생됩니다.

### 

## 5. 악기 변경 기능 ##  
<img src="/img/연주.png" width="600" height="300">

- 드럼스틱 또는 손가락 끝 좌표를 이용해 카메라 화면상의 악기 영역 안으로 움직이면 악기의 소리가 재생됩니다.

### 

## 6. 종료 기능 ##  
<img src="/img/연주.png" width="600" height="300">

- 드럼스틱 또는 손가락 끝 좌표를 이용해 카메라 화면상의 악기 영역 안으로 움직이면 악기의 소리가 재생됩니다.

### 

# 구현 방법
## 1. 손가락 끝 좌표 검출 ##  
<img src="/img/영상변환.png" width="600" height="300">  
<img src="/img/영상이진화.png" width="600" height="300">  

- 카메라 화면의 RGB영상을 YCrCb영상으로 변환하여 손 피부색 영역에 해당하는 범위의 값을 추출해 이진화 합니다.

### 

<img src="/img/손가락끝검출설명.png" width="600" height="300">  

- 손 영역의 외곽선을 검출합니다
- Convex 결함(외곽선 다각형 내의 빈 공간) 검출합니다
- Convex 결함의 깊이를 고려하여 결함의 시작점과 끝점을 이용해 손가락 끝 좌표를 검출합니다

### 

## 2. 특정 색 물체 좌표 검출 ##  
<img src="/img/드럼스틱.png" width="400" height="300">  

- 카메라 화면의 RGB영상을 HSV영상으로 변환하여 빨간색, 또는 파란색 물체의 영역을 검출하고 영역안 픽셀들의 x, y좌표의 평균값을 구해 무게중심 좌표를 검출합니다

### 

# 동영상 링크(이미지를 클릭하면 유튜브 영상으로 이동합니다) #
[![Video Label](https://github.com/emperor5519/AR-instrument/blob/main/img/%EC%9C%A0%ED%8A%9C%EB%B8%8C%EC%8D%B8%EB%84%A4%EC%9D%BC.png)](https://www.youtube.com/watch?v=4u47xhIxIt0&ab_channel=%EC%B5%9C%EC%8A%B9%ED%98%B8)

사람인 이력서에도 동영상이 첨부되어 있습니다  
