# ⚽ AI 기반 축구 영상 분석 및 퍼포먼스 트래킹

## 📝 1. 프로젝트 개요 (Overview)
이 프로젝트는 딥러닝과 컴퓨터 비전 기술을 활용하여 축구 경기 영상에서 **선수들의 퍼포먼스를 자동 분석**하는 솔루션입니다. **YOLO11** 기반으로 객체를 탐지하고, **DeepOcSort 트래커** 및 **포즈 추정** 기법을 결합하여 두 가지 핵심 분석 기능을 제공합니다.

| 분석 모듈 | 핵심 기능 |
| :--- | :--- |
| **슛팅 카운트** | 선수의 무릎 각도 변화 및 선수와 공의 거리를 분석하여 **자동 슛팅 횟수 카운팅** |
| **선수 추적** | 경기장 내 모든 선수의 **실시간 이동 경로 추적** 및 시각화 |

## ✨ 2. 주요 기능 및 특징 (Features)
* **최신 기술 적용:** **Ultralytics YOLO11**을 활용하여 높은 정확도와 빠른 속도를 확보했습니다.
* **정밀 포즈 분석:** YOLO Pose Estimation을 이용해 사람의 주요 관절 각도 변화 패턴을 분석하여 슛팅 동작을 판별합니다.
* **고성능 멀티 객체 추적 (MOT):** **DeepOcSort** 트래커와 Re-ID 모델을 사용하여 객체 ID를 안정적으로 유지하며 이동 경로를 시각화합니다.

## 📺 3. 데모 및 결과 
![슛팅 카운팅 데모](demo.gif)

## 🛠️ 4. 기술 스택 (Tech Stack)
| 구분 | 기술 / 모델 | 용도 |
| :--- | :--- | :--- |
| **Detection & Pose** | **Ultralytics YOLO11** (Base Model: `YOLO11x`) | 객체 탐지 (Ball, Human), 포즈 추정 |
| **Tracking** | **Boxmot** (`DeepOcSort`) | 멀티 객체 추적 (MOT) 알고리즘 |
| **Re-Identification**| **OSNet** (`osnet_x0_25_msmt17.pt`) | DeepOcSort Re-ID 기능에 사용 |
| **Language** | **Python** | 코어 개발 언어 |
| **Framework** | **PyTorch, OpenCV** | 딥러닝 백엔드 및 영상 처리 |

---

## 🚀 5. 설치 및 설정 (Installation)

### 5.1. 환경 설정 및 라이브러리 설치
```bash
1. 필수 라이브러리 설치 (버전 고정)
ultralytics (v8.3.143 환경), boxmot (트래킹), opencv 설치
pip install ultralytics==8.3.143 boxmot==12.0.1 pip install opencv-python-headless==4.9.0.80 opencv-contrib-python==4.9.0.80

2. numpy 버전 충돌 방지를 위해 강제 재설치 (코랩 이용 시)
pip install numpy==1.26.4 --force-reinstall
```
### 5.2. 모델 가중치 파일

프로젝트 실행을 위해 다음 4가지 가중치 파일이 필요합니다:
* `soccer_ball.pt` (공 탐지)
* `yolo11x-pose.pt` (포즈 추정)
* `yolo11x.pt` (객체 탐지)
* `osnet_x0_25_msmt17.pt` (Re-ID)

---

## 💻 6. 프로젝트 사용법 (How to Run)
### A. 슛팅 카운팅 실행
1.  **입력 파일:** `soccer/soccer_input/` 폴더에 분석할 동영상 파일을 넣습니다.
2.  **실행:** `soccer/shoot_count.ipynb` 파일을 실행합니다.
3.  **결과:** 분석된 영상은 `soccer/soccer_output/optimized_{input_file_name}.mp4`로 저장됩니다.

### B. 선수 트래킹 실행
1.  **입력 파일:** `soccer_tracking/soccer_input/` 폴더에 분석할 동영상 파일을 넣습니다.
2.  **실행:** `soccer_tracking/tracking.ipynb` 파일을 실행합니다.
3.  **결과:** 분석된 영상은 `soccer_tracking/soccer_output/processed_{input_file_name}.mp4`로 저장됩니다.

---

## 💾 7. 데이터셋 (Dataset)

커스텀 공 탐지 모델 학습에 사용된 데이터셋 정보입니다.

* **데이터셋:** `tracking-ball Computer Vision Dataset`
* **출처:** [Roboflow Universe: tracking-ball](https://universe.roboflow.com/mahendra-nakasi/tracking-ball-nnd9p)
* **라이선스:** CC BY 4.0
  
---

## 📚 8. 참고 자료 및 출처 (References)
* **Ultralytics YOLO11 Docs:** [https://docs.ultralytics.com](https://docs.ultralytics.com)
* **Boxmot (DeepOcSort):** [https://github.com/boxmot/boxmot](https://github.com/boxmot/boxmot)
* **Roboflow:** [Roboflow Universe: tracking-ball](https://universe.roboflow.com/mahendra-nakasi/tracking-ball-nnd9p)

