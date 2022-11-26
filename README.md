# github 블로그 만들기
~~블로그 미리보기~~
이미지 첨부

이런 블로그를 만든 과정을 소개합니다!!


## Contents

- [1.github와 개인 작업파일 연동하기 ](https://github.com/sangrae2325/sangrae2325.github.io#1github%EC%99%80-%EA%B0%9C%EC%9D%B8-%EC%9E%91%EC%97%85%ED%8C%8C%EC%9D%BC-%EC%97%B0%EB%8F%99%ED%95%98%EA%B8%B0)
- [2.블로그 테마 적용하기](https://github.com/sangrae2325/sangrae2325.github.io#2%EB%B8%94%EB%A1%9C%EA%B7%B8-%ED%85%8C%EB%A7%88-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
- [3.추가 기능 구현하기](https://github.com/sangrae2325/sangrae2325.github.io#3%EC%B6%94%EA%B0%80-%EA%B8%B0%EB%8A%A5-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0)
  - [댓글 기능 추가하기](https://github.com/sangrae2325/sangrae2325.github.io#%EB%8C%93%EA%B8%80-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0)
  - [Themes](#themes)
  - [Reverse layout](#reverse-layout)
  - [favicon 추가하기](https://github.com/sangrae2325/sangrae2325.github.io#favicon-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0)
  - [Author](#author)
- [License](#license)


## 1.github와 개인 작업파일 연동하기 

제일 먼저 블로그 만들기를 위해 Githube에 sangrae2325.github.io-라는 repositories를 만들었습니다. 그 후 개인 작업공간으로 `blog`라는 파일을 만들어서 commit,push를 위해 연동을 하려고 했으나 무슨 문제인지 push를 하는 과정에서 에러가 발생했습니다. 무슨 문제인지 파악이 어려웠으나 끝에 발급받고 기록해두었던 토큰이 잘못됐다고 판단했습니다. 그래서 sangrae2325.github.io라는 repositories를 새로 만들어 다시 시도해서 성공했습니다.


## 2.블로그 테마 적용하기

그 다음으로 진행한 일은 만들 블로그의 테마를 적용하는 일이었습니다.
수업에서 알려주신 내용으로는 [jekyll](https://jekyllrb-ko.github.io/docs/)에 들어가서 따라하면 된다고 하셨지만 Gem::FilePermissionError가 발생했습니다. 그래서 [에러 해결하기](https://jojoldu.tistory.com/288)을 참고해서 해결했습니다. 하지만 지킬 설치가 에러로 잘 되지 않았습니다. 
그래서 원인을 찾은 결과 환경변수가 윈도우와는 달리 세팅이 자동으로 되어있지 않다는 것을 알아냈습니다. 
![환경변수 설정](https://user-images.githubusercontent.com/106955624/204083558-a0f2ee02-6f33-48e6-b5de-e5936f926fcf.png)
그래서 다음과 같이 환경변수를 직접 설정해줘서 jekyll을 설치 할 수 있었습니다.
그 후 수업 자료로 제공해주신 사이트에서 적절한 테마를 하나 골라서 다운받았고, `blog`파일에 넣어서 테마를 적용시켰습니다.



## 3.추가 기능 구현하기

기본적으로 블로그를 만들고 이제 추가적인 기능들을 구현했습니다.



### 댓글 기능 추가하기

그 후 댓글 기능을 추가 하는 작업을 진행헀습니다. 
**무엇을 이용했나?** disqus 사이트를 이용했습니다.
제공해주신 pdf에 나오는 과정대로 진행했습니다.
`config.yml`에 `key-value`를 추가하고 `Universal Code`를 복사한후 페이지에 맞게 수정하라는 말이 무슨 말인지 잘 모르겠어서 조금 헤메다 친구들에게 물어봐서 해결 할 수 있었습니다.






### favicon 추가하기

추가로 구현 하라고 하신 것중에 `favicon`이 있었습니다.
그래서 `favicon`이 무엇인지 알아봤습니다.알고 보니 사이트에 접속했을때 뜨는 작은 아이콘이었습니다. 그래서 구글링을 통해 `favicon`추가를 진행했습니다. 알게 된 과정은 다음과 같았습니다.
**1.원하는 이미지 찾기**
**2.favicon icon 만들기**
**3.custom.html 수정**

그런데 과정중에 _head 폴더 > custom.html을 수정해야 하는데 제가 사용한 테마에는 _head폴더가 존재하지 않았고 `head.html`로 있어서 이 파일을 수정했습니다.

```
 <link rel="apple-touch-icon" sizes="180x180" href="assert/apple-touch-icon.png">
  <link rel="icon" type="image/png" sizes="32x32" href="assert/favicon-32x32.png">
  <link rel="icon" type="image/png" sizes="16x16" href="assert/favicon-16x16.png">
  <link rel="manifest" href="/site.webmanifest">
  <meta name="msapplication-TileColor" content="#da532c">
  <meta name="theme-color" content="#ffffff"> 
```
다음과 같은 코드를 사용했습니다.





### Sidebar overlay instead of push

Make the sidebar overlap the viewport content with a single class:

```html
<body class="sidebar-overlay">
  ...
</body>
```

This will keep the content stationary and slide in the sidebar over the side content. It also adds a `box-shadow` based outline to the toggle for contrast against backgrounds, as well as a `box-shadow` on the sidebar for depth.

It's also available for a reversed layout when you add both classes:

```html
<body class="layout-reverse sidebar-overlay">
  ...
</body>
```

### Sidebar open on page load

Show an open sidebar on page load by modifying the `<input>` tag within the `sidebar.html` layout to add the `checked` boolean attribute:

```html
<input type="checkbox" class="sidebar-checkbox" id="sidebar-checkbox" checked>
```

Using Liquid you can also conditionally show the sidebar open on a per-page basis. For example, here's how you could have it open on the homepage only:

```html
<input type="checkbox" class="sidebar-checkbox" id="sidebar-checkbox" {% if page.title =="Home" %}checked{% endif %}>
```

## Development

Lanyon has two branches, but only one is used for active development.

- `master` for development.  **All pull requests should be to submitted against `master`.**
- `gh-pages` for our hosted site, which includes our analytics tracking code. **Please avoid using this branch.**


## Author

**Mark Otto**
- <https://github.com/mdo>
- <https://twitter.com/mdo>


## License

Open sourced under the [MIT license](LICENSE.md).

<3
