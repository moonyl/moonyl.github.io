---
title: 블록 레벨 요소와 인라인 요소
description: 'HTML 소스를 자주 보지는 않지만, 자주 보이는 요소를 바탕으로 블록 레벨 요소와 인라인 요소로 나눠 보고자 합니다.'
date: '2019-02-02T06:04:30.060Z'
categories:
  - web-devel
tags:
  - block-level-element
  - inline-element
  - html
last_modified_at: 2019-02-02T06:04:30.060Z
slug: >-
  /@moony211/%EB%B8%94%EB%A1%9D-%EB%A0%88%EB%B2%A8-%EC%9A%94%EC%86%8C%EC%99%80-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EC%9A%94%EC%86%8C-3a7cd4fa8eb6
---

HTML 소스를 자주 보지는 않지만, 자주 보이는 요소를 바탕으로 블록 레벨 요소와 인라인 요소로 나눠 보고자 합니다.

블록 레벨 요소로는 `<div>, <form>, <h1>` 계열, `<header>, <hr>, <li>, <nav>, <ol>, <p>, <pre>, <table>, <ul>` 등이 있습니다.

인라인 요소로는 `<b>, <i>, <a>, <br>, <img>, <span>` 등이 있습니다.

직관적으로 보이는 차이점은 전자는 하나의 태그가 완료가 되면, 줄바꿈이 일어나는 반면, 후자는 그대로 유지가 된다는 점입니다. 줄바꿈이 일어난다는 자체가 블록이라는 개념으로 대표가 되고, 그 줄이 유지된다는 의미로 인라인이라는 용어를 사용한 듯 합니다.

이 요소는 display라는 특성에 속합니다. 즉, display라는 속성에 block과 inline이라는 구분이 존재한다고 할 수 있습니다.

CSS를 통해서 요소의 display 속성을 변경해서 다르게 동작하도록 만들 수 있습니다. 풀어서 얘기하면, `<h1>`을 인라인 요소로, `<a>`를 블록 레벨 요소로 동작하도록 만들 수 있다는 의미입니다. 각 요소에 display 속성이 디폴트 값으로 정해져 있을 뿐, 상황에 따라 변경해서 사용할 수 있다는 말이 됩니다.

CSS를 이용해서 h1과 a 태그에 대해 영역을 표시하도록 해 봤습니다.

h1 태그의 범위는 한 줄 전체를 나타내는 반면, a 태그의 범위는 그것 내에 컨텐츠에만 국한해서 나타납니다.

![](/assets/img/1__EAV__FKwdqa__O1zVTPlWCSA.png)

두 태그에 대해 display 속성에 대한 값을 바꿔보도록 하겠습니다.

결과 화면은 재미있습니다. 선택 범위에서 이제 h1이 컨텐츠 범위까지만, a는 한 줄 전체를 덮는 결과를 보여줍니다. 특히, h1 태그가 인라인 요소로 바뀌는 바람에 다음 줄에 나타나던 문장이 붙어서 표현됩니다.

![](/assets/img/1__PjDvuQOv8SWcyTKix6za3Q.png)

이 정도면 블록 레벨 요소와 인라인 요소의 차이를 알 수 있을 것 같습니다.