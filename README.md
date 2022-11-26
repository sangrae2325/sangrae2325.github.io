# github 블로그 만들기



Lanyon is an unassuming [Jekyll](http://jekyllrb.com) theme that places content first by tucking away navigation in a hidden drawer. It's based on [Poole](http://getpoole.com), the Jekyll butler.

![Lanyon](https://f.cloud.github.com/assets/98681/1825266/be03f014-71b0-11e3-9539-876e61530e24.png) 
![Lanyon with open sidebar](https://f.cloud.github.com/assets/98681/1825267/be04a914-71b0-11e3-966f-8afe9894c729.png)


## Contents

- [1.github와 개인 작업파일 연동하기 ](https://github.com/sangrae2325/sangrae2325.github.io#1github%EC%99%80-%EA%B0%9C%EC%9D%B8-%EC%9E%91%EC%97%85%ED%8C%8C%EC%9D%BC-%EC%97%B0%EB%8F%99%ED%95%98%EA%B8%B0)
- [2.블로그 테마 적용하기](https://github.com/sangrae2325/sangrae2325.github.io#2.%EB%B8%94%EB%A1%9C%EA%B7%B8-%ED%85%8C%EB%A7%88-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)
  - [Sidebar menu](#sidebar-menu)
  - [Themes](#themes)
  - [Reverse layout](#reverse-layout)
- [Development](#development)
- [Author](#author)
- [License](#license)


## 1.github와 개인 작업파일 연동하기 

제일 먼저 블로그 만들기를 위해 Githube에 sangrae2325.github.io-라는 repositories를 만들었습니다. 그 후 개인 작업공간으로 '<blog>'라는 파일을 만들어서 commit,push를 위해 연동을 하려고 했으나 무슨 문제인지 push를 하는 과정에서 에러가 발생했습니다. 무슨 문제인지 파악이 어려웠으나 끝에 발급받고 기록해두었던 토큰이 잘못됐다고 판단했습니다. 그래서 sangrae2325.github.io라는 repositories를 새로 만들어 다시 시도해서 성공했습니다.


## 2.블로그 테마 적용하기

그 다음으로 진행한 일은 만들 블로그의 테마를 적용하는 일이었습니다.
수업에서 알려주신 내용으로는 [jekyll](https://jekyllrb-ko.github.io/docs/)에 들어가서 따라하면 된다고 하셨지만 Gem::FilePermissionError가 발생했습니다. 그래서 [에러 해결하기](https://jojoldu.tistory.com/288)]을 참고해서 해결했습니다. 하지만 지킬 설치가 에러로 잘 되지 않았습니다. 
그래서 원인을 찾은 결과 환경변수가 윈도우와는 달리 세팅이 자동으로 되어있지 않다는 것을 알아냈습니다. 
![환경변수 설정](http://drive.google.com/uc?export=view&id=1uRUEyem__YPnTaPoVJQBfSDddC4qFqUf_link)
그래서 다음과 같이 환경변수를 직접 설정해줘서 jekyll을 설치 할 수 있었습니다.




### Sidebar menu

Create a list of nav links in the sidebar by assigning each Jekyll page the correct layout in the page's [front-matter](http://jekyllrb.com/docs/frontmatter/).

```
---
layout: page
title: About
---
```

**Why require a specific layout?** Jekyll will return *all* pages, including the `atom.xml`, and with an alphabetical sort order. To ensure the first link is *Home*, we exclude the `index.html` page from this list by specifying the `page` layout.


### Themes

Lanyon ships with eight optional themes based on the [base16 color scheme](https://github.com/chriskempson/base16). Apply a theme to change the color scheme (mostly applies to sidebar and links).

![Lanyon with red theme](https://f.cloud.github.com/assets/98681/1825270/be065110-71b0-11e3-9ed8-9b8de753a4af.png)
![Lanyon with red theme and open sidebar](https://f.cloud.github.com/assets/98681/1825269/be05ec20-71b0-11e3-91ea-a9138ef07186.png)

There are eight themes available at this time.

![Available theme classes](https://f.cloud.github.com/assets/98681/1817044/e5b0ec06-6f68-11e3-83d7-acd1942797a1.png)

To use a theme, add any one of the available theme classes to the `<body>` element in the `default.html` layout, like so:

```html
<body class="theme-base-08">
  ...
</body>
```

To create your own theme, look to the Themes section of [included CSS file](https://github.com/poole/lanyon/blob/master/public/css/lanyon.css). Copy any existing theme (they're only a few lines of CSS), rename it, and change the provided colors.


### Reverse layout

![Lanyon with reverse layout](https://f.cloud.github.com/assets/98681/1825265/be03f2e4-71b0-11e3-89f1-360705524495.png)
![Lanyon with reverse layout and open sidebar](https://f.cloud.github.com/assets/98681/1825268/be056174-71b0-11e3-88c8-5055bca4307f.png)

Reverse the page orientation with a single class.

```html
<body class="layout-reverse">
  ...
</body>
```


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
