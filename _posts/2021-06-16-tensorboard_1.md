---
layout: single
title: "Tensorboard 활용 (1)"
author_profile: true
excerpt: "remote, tensorboard.dev"
categories:
    - MLOps
---

학습된 결과를 팀원들과 함께 공유하고자 한다면 어떻게 해야할까? 기존에는 call back 함수를 이용해서 epoch마다 accuracy, loss, validation accuracy, validation loss 히스토리를 하나의  csv파일로 저장하고, csv파일을 판다스나 엑셀로 시각화했다. 기존에 텐서보드를 활용하면 자동으로 해준다는 것을 알고 있었지만 어차피 스크린샷 형태로 이미지로 저장하여 리포트를 작성해야 했기에 큰 차이점이 없었다. 하지만 텐서보드를 interactive하게 팀원간에 공유가 가능하다는 것을 알게되었다. 로컬환경에서 텐서보드를 실행한 것과 동일한 웹화면을 다른 사람과  공유할 수 있다는 얘기다. 그럼 하나하나 살펴보자.

 

## 텐서보드 원격 접속

```
ssh -L 6006:127.0.0.1:6006 $USERNAME@SERVER_IP
```

대부분 원격서버에 접속하여 학습된 결과를 로컬환경에서 조회하고 작업을 할 것이다. 원격서버로 접속할 때 위와 같은 명령어를 입력하여 접속한 다음, 텐서보드를 실행하자. 

```
tensorboard --logdir $DIRECTORY_NAME
```

텐서보드를 실행하고  로컬 컴퓨터에서 'localhost:6006' 을 입력하면 텐서보드가 실행된 웹페이지를 볼 수 있다.



## Tensorboard.dev

Tensorboard.dev는 텐서보드 화면을 그대로 다른 사람과 공유할 수 있도록 해주는 도구이다.  구글 서버로 업로드하고 업로드가 완료되면 링크를 보내준다. 해당 링크를 공유하고 싶은 사람에게 보내면 텐서보드 결과를 모두 확인해볼 수 있다. 



### 텐서보드 공유 링크 생성

```
tensorboard dev upload --logdir $DIRECTORY_NAME
```

최초 실행 시 구글계정을 통해서 인증키를 받는다. 구글계정이 있어야 가능하다. ( 단, 텐서보드를 생성하는 사람 외 조회하는 사람은 구글계정이 필요하지 않다. )

인증번호를 입력하면 링크를 받을 수가 있다. 



### 생성된 링크 조회 및 삭제

```
tensorboard dev list # 링크 조회
tensorboard dev delete --experiment_id "EXPERIMENT_ID" # 링크 삭제
```

링크 조회 명령어를 통해 experiment_id 조회가 가능하다.

만약 다른 오류나 문제가 있다면 아래 이메일로 문의 가능하다.

tensorboard.dev-support@google.com

