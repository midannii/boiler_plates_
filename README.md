# making boiler_plates_


`node.js`, `mongoDB` 로 만들어진 boiler plate를 `mysql`로 만들기

`heroku` 를 이용하여 빌드까지 ! ☺️☺️



## workflow (with mongoDB)

- User.js

  - `mongoose`를 이용해 mongoDB에 `User`라는 Model 생성 (`userSchema`)

    - model: schema를 감싸주는 역할 ([schema란?](https://www.zerocho.com/category/MongoDB/post/5963b908cebb5e001834680e))

  - `userSchema`에서 `comparePassword()`, `generateToken()`, `findByToken()` 이용하여 각각의 기능 수행

    - [token 이란?](https://krksap.tistory.com/1586) : '권한'

- index.js

  - `mongoose`를 이용해 mongoDB connect

  - `User`(User.js 에서 만든 model)를 기반으로

    - `회원가입`: new User

    - `로그인`: findOne(), comparePassword(), generateToken()

    - `로그아웃`: findOneAndUpdate()


## workflow (with mysql)

mongoose를 이용해 새로운 객체를 만듦으로서 DB 연결과 회원가입, 로그인, 로그아웃 기능을 함수로 수행하던 `nosql`과 달리,

`sql` 방식은 만들어진 user table에 row를 추가하는 방식으로 회원가입, `select`를 통해 로그인, 로그아웃을 구행한다.

- index.js

  -  `config/DB.js`를 이용하여 mysql DB와 연결   


## heroku usage

after install heroku CLI,

```
$ heroku
$ heroku addons:create cleardb:ignite -a movie-minjok
$ heroku config | grep CLEARDB_DATABASE_URL
$ heroku config:set DATABASE_URL='mysql://adffdadf2341:adf4234@us-cdbr-east.cleardb.com/heroku_db?reconnect=true'
```

이때, `mysql://username:password@host정보/데이터베이스?...`



## Reference

- Boiler Plate 만들기 Youtube 영상 : [En](https://www.youtube.com/watch?v=yScMn7iBa1g&list=PL9a7QRYt5fqly7BrCxOS71BqLLb9OeXKd) , [Ko](https://www.youtube.com/watch?v=fgoMqmNKE18&list=PL9a7QRYt5fqkZC9jc7jntD1WuAogjo_9T)

  - [github](https://github.com/jaewonhimnae/boilerplate-mern-stack)

- [SSH 공개키 만들기](https://git-scm.com/book/ko/v2/Git-%EC%84%9C%EB%B2%84-SSH-%EA%B3%B5%EA%B0%9C%ED%82%A4-%EB%A7%8C%EB%93%A4%EA%B8%B0)

- [Github에 ssh 공개 키 등록](https://brunch.co.kr/@anonymdevoo/10)

- [mysql과 postman 연동](https://medium.com/@Raghwendra.sonu/in-this-story-i-am-going-to-talk-about-how-you-can-connect-to-mysql-database-through-postman-and-8987b1aacca0)

- [mysql과 heroku연결](https://dev-dongwon.github.io/articles/2019-09-03/heroku-mysql)

- [mongoDB를 mysql로](https://stackoverrun.com/ko/q/12550170)

- [mongoose: node.js with mongoDB](https://mongoosejs.com/docs/)

- [node.js with mysql](https://www.npmjs.com/package/mysql)

- [heroku 시작](https://victorydntmd.tistory.com/112)

- [mysql로 로그인, 회원가입 구현](https://m.blog.naver.com/PostView.nhn?blogId=magnking&logNo=221148738767&proxyReferer=https:%2F%2Fwww.google.com%2F)

- [node.js으로 회원가입을 구현하면서](https://so-tired.tistory.com/56)

- [crypto 암호화](https://www.zerocho.com/category/NodeJS/post/593a487c2ed1da0018cff95d)
