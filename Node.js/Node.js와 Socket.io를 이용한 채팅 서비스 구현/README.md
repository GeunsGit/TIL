# TIL 

## 배운점 / 느낀점
- 실습을 하면서 node.js의 개념을 더욱 정립할 수 있었다. 그리고 node.js는 이런 채팅 서비스를 만들고자 할 때 활용성이 높은 것을 알 수 있었다.
- Node.js를 사용해보니 javascript 만으로 간단하게 서버를 만들고 채팅 서비스를 구현할 수 있다는 점이 꽤나 매력적으로 느껴졌다.
- if문이 많아 비동기 방식으로 구현하기 어려울 때는 사용을 지양해야겠다.

## node.js와 socket.io를 활용한 채팅 server / client 구현

- 채팅 애플리케이션을 만들 때, LAMP(PHP)같이 일반적인 웹 애플리케이션 스택으로 만드는 것은 어려운 일이다. 서버에서 변경사항을 가져오고, 타임스탬프를 추적하고 시간이 많이 소요된다.
Socket은 전통적으로 클라이언트와 서버 간의 양방향 통신을 제공하는 실시간 채팅 시스템의 해법이다. 서버는 메시지를 클라이언트에게 푸시할 수 있다.

### Socket.IO
- Socket.IO는 두 가지로 이루어져 있다.
	- Node.js HTTP 서버에 통합되는 서버 : socket.io
	- 브라우저에서 실행되는 클라이언트 라이브러리 : socket.io-client

- 사용하기 위해 socket.io 와 express 모듈을 추가한다.
```
npm install --save --save-exact socket.io express
```


![socket(2)](https://user-images.githubusercontent.com/92859179/174125599-d8e6a786-fb17-471b-a3ae-dbf5380f7324.jpg)
- 위와 같이 package.json에 express와 socket.io 의존성이 추가된 것을 확인할 수 있다.


![socket(1)](https://user-images.githubusercontent.com/92859179/174125538-3207f961-917d-4a6a-bd5d-06be6175fa5b.jpg)
- sockiet.io의 인스턴스를 초기화하고, http 객체에 전달한다.


![socket(3)](https://user-images.githubusercontent.com/92859179/174125664-65d0ef90-6401-40bb-81eb-8f5d78566f54.jpg)
- index.html
- 그런 다음 socket.io-client를 불러오기 위한 코드를 추가한다.
```javascript
<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io();
</script>
```


![socket(4)](https://user-images.githubusercontent.com/92859179/174125673-aa652b05-43ce-4d47-9e37-d56eafa4ad6c.jpg)
- 위와 같이 emit을 통해 채팅 메시지 이벤트로 받게 한다.
- Socket.IO는 모든 사람에게 이벤트를 보내기 위해 io.emit 기능을 제공한다.
```javascript
io.emit('some event', { someProperty: 'some value', otherProperty: 'other value' }); 
```
- 보낸 사람을 포함한 모든 사람에게 메시지를 보내기 위해서는 다음과 같이 작성한다.
```javascript
io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    io.emit('chat message', msg);
  });
});
```

## 최종 코드

![socket(5)](https://user-images.githubusercontent.com/92859179/174125692-428776fc-698c-4bcf-83c7-67c2ff4d8f54.jpg)
- index.js


![socket(6)](https://user-images.githubusercontent.com/92859179/174125702-a1860091-420e-4a69-bae2-f9136dfac49f.jpg)
- index.html의 script


![socket(7)](https://user-images.githubusercontent.com/92859179/174125718-cbe51f68-67ec-4ab7-86b8-49f075c78e0a.jpg)
- localhost:3000 접속


![socket(8)](https://user-images.githubusercontent.com/92859179/174125765-6c286d09-cc93-4058-ba7a-d59c2c7ffcc3.jpg)
- 현재 접속자와 접속자의 참여 표시


![socket(9)](https://user-images.githubusercontent.com/92859179/174125774-a41c15fb-a9be-4185-a041-0f30796ff253.jpg)
- 브라우저 종료시 disconnect 되며, 채팅방에서 퇴장

## Node.js

- Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임이다.
- 서버가 아니라 서버와 같은 네트워크 프로그램을 만들기 위한 S/W 플랫폼이다.

## javascript

- C, C++로 윈도우 프로그램을 만들었다면, 윈도우 OS가 설치된 디바이스에서는 어디든 실행이 가능하다.
- 하지만 javascript를 실행하기 위해서는 웹 브라우저가 반드시 필요하다.

## Node.js를 쓰는 이유?

- javascript는 브라우저에서 동작하기 때문에 브라우저 없이 javascript를 실행하기 위한 실행환경이 필요하다.
- Node.js로 javascript 실행환경의 서버 프로그램을 만들 수 있다.

## Node.js의 특징

- 단일 쓰레드(Single Thread) 이벤트 루프(Event Loop) 기반
- 비동기 Non-Blocking I/O 처리
- 이벤트 발생 시 서버에 메시지 형태로 전달

## Node.js의 장점

- javascript를 사용해서 서버를 만들 수 있다는 점
- npm(node package manager)을 통한 다양한 모듈, 라이브러리 제공

## Node.js의 단점

- 코드의 순차적 실행이 아닌 비동기 방식의 이벤트 처리기 때문에 java 개발 방식으로 설계하고 프로그래밍하면 문제가 발생한다.
- 단일 쓰레드(Single Thread)이기 때문에 하나의 작업 자체가 많이 걸리는 서비스 형태의 경우에는 사용이 불가능하다.

## Node.js의 활용 시기

- 간단한 서버 로직이 필요할 때
- 빠른 응답시간이 요구될 때
- 빠른 개발이 요구될 때
- 비동기방식에 어울리는 **스트리밍 서비스**, **채팅 서비스** 등을 개발할 때

## Node.js를 사용하지 않아야 하는 경우

- 서버 체크로직이 많은 경우 : 분기가 많아서 비동기 방식으로 구현하기 상대적으로 어려운 경우
- 업무 로직의 복잡도/난이도가 높은 경우