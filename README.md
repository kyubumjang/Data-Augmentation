# Data-Augmentation-using-GAN-for-Improving-Pose-Detection

GAN을 사용해서 CCTV 속 이상행동 데이터를 증강하고, 이를 다시 딥러닝 모델에 학습시켜 상황에 대한 구체적 분석이 가능한 개선된 성능의 AI 설계를 시도해봤습니다.

## 프로젝트 개요

- 프로젝트 명: GAN을 이용한 Object Detection Data Augmentation
- 담당 교수님: 배성호 교수님
- 멘토: 장윤호 멘토님
- 팀원
  - 이광원
  - 장규범

## 1. 연구 배경

- 최근 딥러닝 기술의 발전으로 영상분석 기술을 활용한 CCTV의 지능화가 진행되고 있다. 코로나 19 현행 방역지침인 1~2m 거리에 가까워지면 ‘방역 사항 준수 안내’ 알람이 울리고, 마스크 미착용 뿐만 아니라 ‘턱스크’까지 감지하여 경고 문구가 나오기까지 하는 수준에 이르렀다. 사람을 감지하면 옷의 색상, 성별, 나이, 안경 착용 등을 분석하고, 차량의 경우 종류, 색상, 번호 등 구체적인 정보를 감지한다. 또한, 이상행동 및 위험 상황을 감지하여 관련 영상을 관제 요원에게 우선 표출하는 시스템을 구축해 나가고 있다. 이때 사용하는 딥러닝 기술은 다양한 CCTV 영상을 인공지능이 스스로 학습하는 기법으로 다양한 영상을 누적시켜 객체 인식률을 높이고 있다. 지능형 CCTV의 핵심기술인 딥러닝 기술을 적용하기 위해서는 많은 수의 데이터 확보가 필수적이다. 쉽게 모을 수 있는 데이터가 있지만 모으기가 굉장히 어려운 데이터도 존재한다. 적은 양의 데이터는 딥러닝 모델의 정확도를 떨어뜨리는 원인이 된다. 따라서 딥러닝 연구 분야 중 Data Augmentation 분야는 성능을 높이는 데 있어 굉장히 중요한 주제이다. 연구 분야에 있어서 Data Augmentation 분야는 다른 분야에 비해 소홀한 경향이 있었다. 그동안 새로운 자료를 수집하지 않고 다양성을 늘리는 Image 기반의 Data Augmentation 방법을 이용해왔다. 원 이미지를 변형하여 이미지 복사본을 만들어 활용했는데 이런 방식은 GAN이 제대로 된 합성 이미지를 만들어내지 못하고 이미지 변형을 모방 학습하는 상황이 초래될 수 있다. 본 연구에서는 이러한 문제를 해결하기 위해서 Pose-Attentional Transfer Network GAN(PATN GAN)을 활용하여 적은 양의 이상행동 데이터를 Data Augmentation 하여 상황 분석 CCTV 모델의 인식 정확도를 높이고자 한다. 기존 데이터 증강 전 데이터를 학습시킨 모델과 GAN을 이용해 Data Augmentation을 진행한 모델을 비교 분석한다.

## 2. 연구 목표

- CCTV 영상 데이터가 많기 때문에 학습할 데이터 또한 많다고 생각할 수 있지만, 사실 사고 발생 시점의 영상만이 유의미한 학습 데이터라고 할 수 있다. 그러므로 사고 상황의 영상이 더욱 많이 필요하다. 하지만 긴 CCTV 영상들 속에서 사고 순간을 개별적으로 추출하거나, 사고 영상을 얻기 위해 사고가 발생하기를 기다리는 것 또한 현실적이지 못하다. 따라서 우리는 이번 연구를 통해 CCTV 속 이상행동을 기반으로 사고 영상의 데이터를 추출하여, GAN을 통해 데이터를 증강시키고, 데이터 학습을 통해 이상 행동에 대해 인식할 수 있는 상황 인식 CCTV의 성능 개선에 대해 연구하는 것이 목표이다. 구체적인 목표로는 다음과 같다.

1. 첫 번째 목표는 사고 영상 속 행동 데이터 추출하는 것이다. 먼저 사고 원본 영상에서 행동 데이터를 추출해야 그 데이터를 기반으로 행동 데이터를 증강시킬 수 있다. 따라서 객체 탐지 시스템에 대한 연구를 기반으로 우리가 가지고 있는 AI HUB 이상행동 CCTV 영상 데이터 속 이상 행동에 대해 탐지하고 행동 데이터를 추출해내는 것이 첫 번째 목표이다.

2. 두 번째, GAN으로 행동 데이터 증강 시키는 것이다. 추출한 행동 데이터를 기반으로 데이터를 다양한 GAN 모델을 사용하여 데이터를 증강 시킬 것이다. 새로운 증강기술에 대해 연구하여 고품질의 데이터를 원본으로부터 생성해서 데이터를 증강시키는 것이 두 번째 목표이다.

3. 세 번째로 데이터 학습으로 높은 행동 인식 정확도를 얻는 것이다. 적은 양으로 데이터를 학습시켰을 때와 Data Augmentation을 진행한 후 학습시킨 때를 비교하여 성능이 어느 정도 좋아졌는지, 유의미하게 데이터를 증강시켰는지 확인하는 것이 세 번째 목표이다.

## 3. 프로젝트 역할 분담

1. Object Detction: 이광원
2. Pose Estimation: 이광원
3. 데이터 신청 및 전처리: 장규범
4. 상황 분석 CCTV 모델: 장규범

## 4. 활동내용

1. 객체 추적

   - 컴퓨터 비전 기반 모션 추적
   - 딥러닝 기반 실시간 다중 객체 추적
   - Person Re-Identification

2. 객체 인식

   - COCO Dataset
   - Pose-estimation
     - Open Pose
     - Alpha Pose

3. GAN을 이용한 Data Augmentation

   - DC GAN
   - Keypoint-Guided GAN
     - C2 GAN
     - Crossing(Xing) GAN
     - Variational U-Net

4. 사용한 영상 데이터

   - AI HUB 공항 이상행동 CCTV 영상: 공항 출입국관리 구역 내에서 발생할 수 있는 다수의 움직이는 사람의 신원을 자동으로 식별하고, 위험 상황을 실시간으로 탐지하는 인공지능 시스템 구축, 실증, 검증 지원 및 육성 과제로 인공지능 식별, 추적 시스템의 공항 출입국 관리 실증 적용을 위한 자체 학습 데이터 가공 및 제작하여 제공하고 있다. 제공 데이터 량은 10,000컷 비디오 데이터셋 촬영을 하였고, alchera 이상행동 데이터, nabi 이상행동데이터의 4가지 이상행동(돌진하는 행위, 역방향 이동, 물건을 놓고 사라지는 유기, 2인 감지), cubox 이상행동데이터의 8가지 이상행동(돌진, 방치, 2인감지, 역방향, 정상, 실신, 파손, 폭행)에 대한 데이터를 제공한다.

5. 상황 분석 CCTV 모델 만들어서 원본 데이터를 사용한 인식률과 GAN을 이용한 Data Augment가 진행된 데이터의 인식률 결과 분석

   - CCTV를 계속 보고 감시하는 일은 매우 소모적이고 지루한 일임에도 불구하고, CCTV 카메라의 수와 중요성은 날이 갈 수록 증가하고 있다. 따라서 사람이 CCTV를 계속 보고 있지 않아도 되도록 딥 러닝과 관련된 연구가 감시카메라 영역에도 발전되어 졌다. Avenue Dataset을 사용한 이상 행동 관측 연구에서는 인코더와 디코더로 이루어진 3D Neural Network을 사용해 reconstruction loss를 구하고 이상 행동 여부를 구분했다. 학습한 모델을 바탕으로 실시간으로 이상 행동이 발생하면 ‘Abnormal Event’라는 알림을 보낸다.

   - 문제점: 이상 행동 분석에 필요한 데이터는 다른 Classification Problem들과 비교하여 데이터가 매우 부족하고 카메라의 위치와 각도, 주변 환경, 등의 요소에 따른 변인이 너무 많이 발생한다. 또한 이상 행동을 인식해도 ‘Abnormal Event’라는 알림을 보낼 뿐 어떠한 상황인지는 알지 못한다.

   - 해결방안: Pose Estimation을 사용해서 다른 요소를 배제하고 사람의 행동 데이터 만을 추출하기 때문에 여러 환경에서 적용 가능한 유의미한 학습 데이터와 정확성을 얻을 수 있다. 또한 Pose-Attentional Transfer Network GAN(PATN GAN)을 사용함으로써 실제와 비슷한 학습 데이터를 생성할 수 있으므로 학습 데이터 부족 문제를 해결할 수 있고 상황에 대한 분석(Classification)이 가능해질 것이다.

## 5. 결론

## 6. 문서 및 보고서

- 주간 보고서

- 면담 보고서

- 기초 조사서

- 중간 보고서

- 최종 보고서
