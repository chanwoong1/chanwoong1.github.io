---
title: '우테코 프리코스 2주차'
date: '2022-11-08'
tags: ['javascript', 'woowacourse']
draft: false
summary: 숫자 야구 게임을 만들어보자.
layout: PostSimple
---

이전 글

- [우테코 시작](https://chanwoong1.github.io/blog/woowacourse/precourse_main)
- [1주차](https://chanwoong1.github.io/blog/woowacourse/precourse_week1)

이번 주의 과제는 숫자 야구 게임이다. 숫자 야구 게임이란, 1부터 9까지의 숫자를 3개 골라, 상대방이 고른 숫자를 먼저 맞추는 게임이다. 이번 과제에서는 컴퓨터가 무작위로 숫자를 뽑으면, 사용자가 맞출 수 있도록 만들어야한다.

숫자 야구의 룰은 상대방의 숫자를 맞출 때, 3개의 숫자 모두 맞추지 못하면 '낫싱', 숫자는 포함되지만 위치가 다르면 '볼', 숫자와 위치를 다 맞추면 '스트라이크'로 3스트라이크가 되어야 게임을 끝낼 수 있다.

이번 과제는 1주차의 공통피드백을 충분히 숙지하고 진행하기로 했다. 또한, git_flow 전략을 사용하여 개발하며 커밋메세지 또한 의미있게 작성하려 노력했다.

먼저, 구현할 기능 목록을 작성하였다. 기능 목록을 상세하게 작성하여 단계별, 기능별로 커밋을 하려 노력했다.

## 기능 구현 목록

1.  게임 진행 순서에 따른 콘솔 입출력 구현

    1-1. 실행 시 콘솔에 '숫자 야구 게임을 시작합니다.'라는 게임 시작 문구를 출력합니다.

    1-2. '숫자를 입력해주세요 : '를 출력하며 숫자를 입력받습니다.

    1-3. 숫자를 입력받을 때, 유효한 입력값을 판단합니다.
    1-3-1. 만약 유효한 입력값이 아니라면 'throw'문을 사용하여 예외를 발생시키고 애플리케이션을 종료시킵니다.

    1-4. 유효한 입력값이 들어왔을 경우, 상황에 알맞는 출력을 합니다.

        1-4-1. 3스트라이크로 종료되지 않는 경우, 상황에 맞는 볼, 스트라이크, 낫싱을 출력하고 1-2로 돌아갑니다.

        1-4-2. 3스트라이크인 경우 '3개의 숫자를 모두 맞히셨습니다! 게임 종료'를 출력합니다. 그리고 사용자의 재시작 의사를 판단하는 값 [1, 2]를 받습니다.

        	1-4-2-1. 만약 유효하지 않은 값이 들어온다면 다시한번 재시작 의사 판단 값을 입력 받습니다. 1-4-2로 돌아갑니다.

        	1-4-2-2. 1의 값을 받았다면 재시작으로 1-2로 돌아갑니다.

        	1-4-2-3. 2의 값을 받았다면 애플리케이션을 종료합니다.

2.  게임 진행 유틸리티 구현

    2-1. 게임을 진행하기 위해 컴퓨터가 1~9의 범위에서 임의의 값 3개를 가질 수 있도록 구현합니다.

    2-2. 1-2의 상황에서 입력값을 받았을 경우, 입력값을 판단하는 기능을 구현합니다. 입력값 판단 기능은 다음과 같습니다.

        2-2-1. 먼저, 입력값은 string 타입으로 들어오므로, 문자의 길이가 3인지 아닌지 판단합니다.

        2-2-2. 문자의 길이가 3이라면 문자를 배열로 변환하여 각 요소를 검사합니다.

        2-2-3. 각 요소가 숫자인지 판단합니다. '1'부터 '9'까지의 범위 내에 존재하는지 판단합니다.

        2-2-4. 사용자가 입력한 값 중 중복되는 숫자가 존재하는지 확인합니다. 중복이 존재하지 않아야합니다.

        2-2 의 조건 중 하나라도 조건이 충족되지 않는다면 유효한 값이 아니라고 판단하고 애플리케이션을 종료하도록 합니다. (1-3-1) 수행

    2-3. 유효한 값이 들어왔다면, 배열로 변환된 사용자의 값이 컴퓨터의 값에 포함되어있는지 확인합니다. (볼 판단)

    2-4. 볼 판단이 완료되었다면, 볼 중 컴퓨터의 인덱스와 사용자의 인덱스가 같은 경우 스트라이크로 판단하여 볼에서 1 빼주고 스트라이크를 1 더해줍니다.

위와 같은 형식으로 구현할 기능을 나누어 주었다. 이대로만 하면 되겠다 싶었으나...

콘솔을 통해 입력값을 받는 작업이 우테코에서 제공하는 라이브러리를 사용해야 했고, 콜백함수로 구현이 되어있었다.

콜백함수는 봐도봐도 헷갈리는 부분이 있어서 다시한번 정리해놓은 글을 읽으면서 이해하려 노력했다. ([콜백함수 정리글](주소적기))

이후, 콜백함수를 통해 입력값을 받고, 콜백함수 내부에서 모든 상황 처리를 해주는 형식으로 코드를 구성했다. 또한, 기능 구현 목록이 보기 힘든것 같아서 간략하게 바꿔주었다.

1. 야구 게임 시작 문구를 출력합니다. ('숫자 야구 게임을 시작합니다.')

2. 상대방(컴퓨터)에게 임의의 세자리 숫자를 할당해줍니다.

3. 사용자에게 숫자를 입력받습니다. ('숫자를 입력해주세요 : ')

4. 입력받은 숫자를 검증합니다. (유효하지 않은 입력값이라면 예외를 발생시킵니다.)

5. 검증된 입력값에 대해 결과를 출력합니다. ('낫싱', '볼', '스트라이크')

6. 5번 기능이 '3스트라이크'를 출력할 때 까지 기능을 반복합니다. (3 ~ 5번 기능 빈복)

7. 5번 기능이 '3스트라이크'를 출력하면 게임 종료 문구를 출력합니다. ('3개의 숫자를 모두 맞히셨습니다! 게임 종료')

8. 재시작 여부를 묻는 문구를 출력하고, 값을 입력받습니다. ('게임을 새로 시작하려면 1, 종료하려면 2를 입력하세요.)

9. 8번 기능으로 1을 입력받았다면 2번 기능부터 동작을 반복합니다.

10. 8번 기능으로 2를 입력받았다면 애플리케이션을 정상 종료합니다.

이런식으로 바꾸어 주었고, 예외사항은 따로 적어주었다.

## 예외 사항

- 입력값의 길이는 3이어야 합니다.
- 세자리의 입력값은 1부터 9까지의 자연수만을 값으로 가집니다.
- 입력값들은 서로 중복되지 않아야합니다.
- 8번 기능으로 [1, 2]의 값만 받을 수 있습니다.

그리고 pull request 전 체크사항을 만들어 제출 전 다시한번 코드를 점검해주었다.

## PR 전 체크사항

- [ ] README.md에 구현할 기능 목록을 정리해서 추가했는가
- [ ] 코딩 컨벤션을 지키며 프로그램을 구현했는가
- [ ] 들여쓰기를 2 spaces로 구현했는가
- [ ] indent는 2까지만 사용했는가
- [ ] process.exit()를 호출하지 않았는가
- [ ] 비정상적 입력에 대해서는 throw로 예외를 발생시켰는가
- [ ] jest를 이용하여 입력과 진행에 대한 테스트를 충분히 수행하였는가
- [ ] Random 및 Console API를 사용하여 구현했는가
- [ ] 프로그래밍 요구 사항을 모두 따랐는가
- [ ] PR을 보내고 과제를 제출했는가

기능 구현을 마치고, 코드의 대략적인 진행사항을 그림으로 나타내보았다.

![Alt text](https://github.com/chanwoong1/chanwoong1.github.io/blob/main/public/static/images/blog_posts/woowacourse/precourse_week2_diagram.png?raw=true)

최종적으로는 이런 플로우로 과제를 구현할 수 있었다.

이번 과제에서는 콜백함수 외에도 많은 것들을 배울 수 있었다. 먼저 클래스의 사용으로, 지금까지 코딩을 하면서 c 혹은 파이썬을 주로 사용했던 터라, 클래스를 통해 과제를 수행하는 것이 생각보다 어려웠다. 그렇지만, 클래스와 메서드를 사용하는것이 함수를 여러개 사용하는것보다 훨씬 가독성이 뛰어나다는 것을 알 수 있었다.

두번째는 깃 플로우 전략과 명확한 커밋 메세지를 활용한 기능별 커밋을 통해 코드 병합과 관리를 더 수월하게 할 수 있었다. 지금까지는 혼자 작업해오면서 커밋을 의미없이 생각나는대로 혹은 하루가 끝이 날 때 주로 했었는데, 이런 습관 때문에 어떤 의도로 어디까지 코드를 작성했는지 한눈에 알아보기가 쉽지 않았다. 저번 주차에 말했듯 이번에는 깃 플로우 전략을 함께 사용하며 기능별 커밋을 해보았는데, 내가 어디까지 기능을 구현했는지 커밋을 통해 알 수 있어서 더 수월하게 과제를 진행할 수 있었다.

세번째는 단위 별 테스트 사용이다. 테스트 코드를 통해 내가 구현한 기능이 어떤 부분에서 문제가 발생하는지 빠르고 정확하게 알 수 있었고, 기능별 테스트는 테스트를 더 심층적으로 진행할 수 있게 해 주었다. 또한, 기능별 테스트 케이스를 추가하며 어떤 예외 사항이 들어갈 수 있는지 더 고민해볼 수 있었고, 이 고민은 기능 구현을 할 때 예외처리를 더 상세하게 할 수 있도록 도와주었다.

벌써 4주의 기간 중 2주의 시간이 흘러가고 있는데, 깊게 고민하며 코딩을 하는것에 대한 즐거움을 느낄 수 있었던 시간이 되었고, 그동안 크게 생각하지 않았던 부분들(코드 컨벤션, 깃 커밋 메세지 등)에 대해서도 많이 생각해볼 수 있어서 나에게 이 프리코스는 좋은 경험으로 남을 것이다.
