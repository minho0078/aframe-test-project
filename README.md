# 프로젝트 구성 내용 요약
본 테스트 프로젝트는 
A-Frame Boilerplate + http-server 의 조합으로 구성되었음.

설치 순서는 
1) A-Frame Boilerplate 설치 (아래 내용 있음)
2) npm install http-server --save-dev
3) mkdir conf
4) cd conf
5) openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem
6) package.json 의 scripts 에 내용 추가
- "serve": "http-server -S -C conf/cert.pem -K conf/key.pem"
7) npm run serve

*openssl 이 없을 경우 아래 링크에서 설치!
- http://slproweb.com/products/Win32OpenSSL.html
- 본 프로젝트 학습 당시에는 Win64OpenSSL-1_1_0h.exe 로 설치했음.
- 그리고 환경설정에서 path에 openssl 추가! (예 > C:\OpenSSL-Win64\bin )
- 다되었으면 5)부터 시작!


8) 패턴은 아래 링크에서 생성!
- 파워포인트 같은 걸루 이미지 간단하게 만들어서 이미지파일로 만든 후 아래 페이지에서 UPLOAD!
- 결과물로 patt 확장자를 갖는 패턴파일 하나랑 프린트 해서 마커로 사용할 이미지 파일을 다운로드 할 수 있음! (pdf도 있는듯!)
- https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html

9) 마커에 나타나는 도형에 이미지 입히기
- https://aframe.io/docs/0.8.0/primitives/a-image.html 에 힌트가 가득함! 그냥 이거 보면 쉽게 할 수 있음!
- 그래도 설명을 하자면, 이미지는 <a-assets> 태그와 <img> 태그로 맹금.
- 그리고 a-box 태그의 id를 <a-image> 태그에 # + id 형태로 입력하면 이미지가 해당 박스객체에 입혀짐.


10) 커스텀 마커 작동 시키기
<a-marker-camera preset='jhs' type='pattern' url='patt/pattern-jhs.patt'></a-marker-camera>
- 공식문서나 구글에 a-marker-camera 만 쳐도 attribute 가 의미하는 바는 알 수 있으니 패스함.
- url에 patt/pattern-jhs.patt 파일을 링크시켜주면 끝! 여기서 patt 는 프로젝트 root 위치에 생성된(1depth) 폴더임.


# ar.js 설치 참고 github site
- ar.js 구글링 해서 사이트 띄우고 모바일 크롬이나 사파리로 접속해보면
- 어? 왜 안되지 할때가 있음. 이유는 서버가 띄워진 프로토콜이 https 가 아니라서...ㅠ
- https 로 서버를 띄우기 위한 솔루션이 있는 깃헙사이트 임. 참고!!
- https://gist.github.com/mritzco/18dfe13096294592d5eb53e7e1a5f63c

# A-Frame Boilerplate

Boilerplate for creating WebVR scenes with [A-Frame](https://aframe.io).

Alternatively, check out the [A-Frame Starter on
glitch.com](https://glitch.com/~aframe) for a more interactive way on getting
started.

## Getting Started

There are two easy options for obtaining this A-Frame scene. It's then up to you to make it your own!

### <sup>Option 1:</sup> Download the ZIP kit 📦

[<img src="http://i.imgur.com/UVPZoM0.png" width="200">](https://github.com/aframevr/aframe-boilerplate/archive/master.zip)

After you have __[downloaded and extracted this `.zip` file](https://github.com/aframevr/aframe-boilerplate/archive/master.zip)__ containing the contents of this repo, open the resulting directory, and you'll be have your scene ready in these few steps:

    npm install && npm start
    open http://localhost:3000/

<hr>

### <small><sup>Option 2:</sup> Fork this Git repo 🍴🐙

Alternatively, you can __[fork this repo](https://github.com/aframevr/aframe-boilerplate/fork)__ to get started, if you'd like to maintain a Git workflow.

After you have __[forked this repo](https://github.com/aframevr/aframe-boilerplate/fork)__, clone a copy of your fork locally and you'll be have your scene ready in these few steps:

    git clone https://github.com/aframevr/aframe-boilerplate.git
    cd aframe-boilerplate && rm -rf .git && npm install && npm start
    open http://localhost:3000/

> :iphone: **Mobile pro tip:** Upon starting the development server, the URL will be logged to the console. Load that URL from a browser on your mobile device. (If your mobile phone and computer are not on the same LAN, consider using [ngrok](https://ngrok.com/) for local development and testing. [Browsersync](https://www.browsersync.io/) is also worth a gander.)

<hr>

### <small><sup>Option 3:</sup> Fork this CodePen example 🍴💾✒️

Or, you can simply __[fork this CodePen example](http://codepen.io/team/mozvr/pen/BjygdO?editors=100)__ to dive right in. Enjoy!


## Publishing your scene

If you don't already know, GitHub offers free and awesome publishing of static sites through __[GitHub Pages](https://pages.github.com/)__.

To publish your scene to your personal GitHub Pages:

    npm run deploy

And, it'll now be live at __http://`your_username`.github.io/__ :)

<hr>

To know which GitHub repo to deploy to, the `deploy` script first looks at the optional [`repository` key](https://docs.npmjs.com/files/package.json#repository) in the [`package.json` file](package.json) (see [npm docs](https://docs.npmjs.com/files/package.json#repository) for sample usage). If the `repository` key is missing, the script falls back to using the local git repo's remote origin URL (you can run the local command `git remote -v` to see all your remotes; also, you may refer to the [GitHub docs](https://help.github.com/articles/about-remote-repositories/) for more information).

<hr>

## Still need Help?

### Installation

First make sure you have Node installed.

On Mac OS X, it's recommended to use [Homebrew](http://brew.sh/) to install Node + [npm](https://www.npmjs.com):

    brew install node

To install the Node dependencies:

    npm install


### Local Development

To serve the site from a simple Node development server:

    npm start

Then launch the site from your favourite browser:

[__http://localhost:3000/__](http://localhost:3000/)

If you wish to serve the site from a different port:

    PORT=8000 npm start


## License

This program is free software and is distributed under an [MIT License](LICENSE).
