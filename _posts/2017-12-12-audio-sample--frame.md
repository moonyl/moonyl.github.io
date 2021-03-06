---
title: Audio sample과 frame
description: >-
  이전부터 정리하고 머릿속에 박아 넣어둬야지 하면서, 차일피일 미뤄두던 일을 드디어 하게 된 것 같다. 학교 때 신호처리 이론을 배운 이후로
  대충 이럴 것이다라는 생각만 가지고 있었고, 코딩을 할 때는 copy & paste 신공으로 보통 해결이…
date: '2017-12-12T21:44:17.584Z'
categories:
  - theory
tags:
  - audio
  - audio sample
  - frame
last_modified_at: 2017-12-11T17:10:28.564Z
slug: /@moony211/audio-sample%EA%B3%BC-frame-e268e33db8f5
---

이전부터 정리하고 머릿속에 박아 넣어둬야지 하면서, 차일피일 미뤄두던 일을 드디어 하게 된 것 같다. 학교 때 신호처리 이론을 배운 이후로 대충 이럴 것이다라는 생각만 가지고 있었고, 코딩을 할 때는 copy & paste 신공으로 보통 해결이 되다보니 게으름이 매번 승리하고 있었다.

동영상이든 음악 파일이든 오디오가 포함되어 있고, 이에 대한 정보로 44100 Hz혹은 44.1KHz 라는 표시가 되어 있다. 이 의미는 초당 441000번으로 오디오 데이터를 샘플링했다는 의미가 된다. 샘플링을 많이 할 수록 원음에 가까운 소리로 복원할 수 있다. 44.1KHz 는 CD 음질로 사용된다. 오디오 관련 코딩을 할 때 sample rate라는 말이 자주 등장하는데, 44100 이라는 값이 바로 이것을 의미한다.

오디오를 렌더링할 때는 물론 하나의 소리만 줄기차게 낼 수 있겠지만, 좌우로 귀가 둘인 사람들을 위해서, 두 개의 채널로 각각 다른 소리를 나오도록 할 수도 있다. 전자를 모노, 후자를 스테레오라고 표현한다. 요즘은 입체적인 소리를 구현하기 위해서 5.1 채널로 구성한 경우도 볼 수 있는데, 총 6개의 채널을 사용한 경우이다. 오디오 데이터는 이 채널이라는 개념을 포함해서 구성을 해야 한다. 채널을 모두 합쳐서 하나의 샘플을 구성하고 있는 것을 프레임(frame)이라고 한다. 즉, 44100Hz 의 sample rate 으로 만들어진 오디오에는 초당 44100개의 frame 이 포함되어 있으며, 모노인 경우에는 sample 의 개수가 frame 의 개수와 동일하고, 스테레오인 경우에는 sample 의 개수가 88200개가 되는 것이라 생각하면 될 것 같다.

하나의 오디오 샘플을 만들 때 얼마나 세밀하게 하느냐에 따라서 하나의 샘플 크기가 결정된다. 양자화라는 전문 용어를 쓰기도 하는데, 이런 건 별로 중요하지 않다. 샘플 하나를 1 byte 로 표현할 것인가, 2 byte 로 표현할 것인가, 이런 내용이다. 1 byte로 표현하면, 하나의 샘플이 256 단계, 2 byte로 표현하면 65536 단계로 나눠서 소리를 재현할 수 있으니, 잘게 나눠 놓은 것이 더 원음의 가까운 소리를 낼 수 있을 것이다. 이렇게 몇 바이트로 잘게 쪼갰느냐 하는 것이 샘플 크기(sample size)이고, 결국 프레임의 크기(frame size)라는 것은 채널과 샘플 크기를 합쳐서 나타내는 말이 된다. 예를 들어, 스테레오의 2 byte 샘플 크기로 표현되는 오디오의 frame size 는 2 \* 2 = 4 byte 가 된다.

데이터 전송량을 측정할 때, bps(bits per second) 를 이용한다. 만약 이 개념들을 정리해서 사용하자면, 4 byte의 floating point 를 사용하며 48K sample rate 으로 5.1 채널용으로 구성된 오디오 데이터의 bps 를 생각해 본다면, 4 \* 48000 \* 6 = 1152000 Bytes/sec = 9216000 bps 가 될 것이다. 초당 9 MBytes 가 넘는 데이터량이라면 상당히 큰 값인 것 같다. 그러나, 오디오나 비디오는 압축해서 처리를 하기 때문에, 전송 시에는 훨씬 데이터량이 작을 것이다.