# WeTube

Cloning Youtube with Vanilla and NodeJS

- middleware안에 next()가 아닌 response를 받으면 서버가 끊긴다.

when somebody filles a form and sends it to you,
this form should be received by the server.

ex) name, pw => server(special data form) => "body-parser"
"body-parser" helps you get the information from the body.

# SERVER needs to know what we are sending !!!

=> bodyParser.json([options]) , bodyParser.text([options]), bodyParser.urlencoded([options])
=> 이게 서버가 유저로부터 받은 데이터를 이해하는 방법이다.

- cookie-parser
  => To 'save' the user information in the cookie,
  => To be able to handle some session

M model \*data

V view \*how does the data look

C controller \*function that looks for the data

URL using routers
the function that executes them (controller)

controller is just basically logic for WHY it happens, HOW it happens,

=================================================
RECAP:
init.js에는 app.js에서 import 한 application이 있다.

- express를 import함.
- express를 실행한 결과를 app으로 만듬. 그리고 middleware를 추가함.

\*COOKIE-PARSER
cookie를 전달받아서 사용할 수 있도록 만들어주는 middleware.
사용자 인증 같은 곳에서 쿠키를 검사할 때 사용함.

\*BODY-PARSER
사용자가 웹사이트로 전달하는 정보들을 검사하는 middleware.
request 정보에서 form이나 json형태로 된 body를 검사한다.
ex)
아바타의 사진이나 비디오를 업로드 할 때,
제목이나 댓글 같은 정보를 전달 할 때, form에 담아서 업로드 해야 한다.

\*HELMET
application이 더 안전하도록 만들어준다.

\*MORGAN 미들웨어의 역할은 application에서 발생하는 모든 인들을 logging한다.

ROUTER 3개 사용한다.
-globalRouter
(/home, /search, /join, /login, /logout URL)

-userRouter
(/user/\*\*\*... 주소들이 담겨있다.)

- 주소들은 모두 routes.js에 정의 한다.
  => 한 파일이 바뀌면 모두 적용되도록 할 수 있다.

-videoRouter

router의 로직들은 CONTROLLER(useController, videoController)에 정의 한다.
=> 모든 함수들이다.(return /join, /userDetail, /logout etc)

\*(pug.js makes HTML sexy)
express로 HTML을 보여줄 수 있다.
res.send 대신에, 실제 HTML을 전달한다.

npm install pug
view engine.

views 폴더 안에 파일을 만든다.
파일명은 home. 확장자는 html대신 pug으로 한다.

res.send() sends things to the user.
res.render() looks into the views folder, takes the template, compiles it and returns the html.

\*PUG
Home 화면과 다른 화면들의 코드가 모두 main 태그 안에 들어가도록 작업한다.

videoController.js => instead of res.send() => res.render('template name')
it will automatically look for pug template because of app.set("view engine", pug)

\*To set up the path
const path = require('path');
app.set('view engine' pug);
app.set('views' path.join(\_\_dirname, 'yourFavoriteDirectory'));

\*PUG
//- EXTENTION 'import from /layouts/main.pug'
//- and then overwrite the block content

app.set('view engine','pug'); -> This tells express that "pug" is the file format to search in the views folder

res.render("home") -> Looks for home.pug in your "views" folder.

It's all done by express for you

\*render
render함수의 첫번째 인자는 템플릿, 두 번째 인자는 템플릿에 추가할 정보가 담긴 객체다.

pageTitle => home 템플릿으로 전달됨.
export const home = (req, res) => res.render("home", {pageTitle : "HOMEControlelr"});

{pageTitle} => "home" template 으로 전달됨.

## Pages:

- [ ] Home
- [x] Join
- [x] Log in
- [x] Search
- [ ] Log out
- [ ] User Detail
- [ ] Edit Profile
- [ ] Change Password
- [ ] Upload
- [ ] Video Edit
- [ ] Edit Video




웹사이트에서 계속 반복되는 코드를 복사-붙여넣기 말고,
재활용 하는 방법 => mixin



monggo db는 C++로 만들어져서 javaScript와 연결 시키려면 adapter가 필요하다.
 
javaScript 코드로 작성하고 싶으면 Mongo DB로 부터 instruction을 받아야 한다.
mongoose => elegant mongodvb object modeling for node.js

**** npm install mongoose

Monggo DB is DataBase
Mongoose connects to DataBase

MongoDB is NoSQL DataBase

MongoDB is good for chatting DB because it's flexible and fast

// 우리가 요청하는건 string으로 된 DataBase다. 어디에 Database가 저장되어 있는지 알려준다.

***** npm install dotenv

dotenv륾 설치한 이유는, 어떤 부분을 숨기고 싶을 때.
ex)to Protect user's data(password, id) from other people.


*** mongod should be running. and then you can access "mongo" 

MongoDB is json.file
.env 안에 ';' 들어가면 => can't read database 

file을 upload하고 URL을 반환할 middleware가 필요하다. => multar

***npm install multer***
enctype="multipart/form-data"
그리고 UPLOAD Form의 enctype에 multipart/form-data를 추가해야 한다.

file을 보낼 때, form의 encoding이 달라야 한다.

Multer is a node. js middleware for handling multipart/form-data , which is primarily used for uploading files.

Multer will not process any form which is not multipart 

TERMINAL

To remove data

1. mongo
2. use <database_name>
3. show collections <show collections in current database>
   => videos
    *collections is like model
4. db.videos.remove({}) => "WriteResult({ "nRemoved" : 1 })"
5. app.use("/uploads", express.static());
     express.static() is a built-in middleware.
        middleware for sending files from directory .


gitignore, uploads숨김.     

https://www.coffeecup.com/help/articles/absolute-vs-relative-pathslinks/

You must use absolute paths when linking to another Website, but you can also use absolute paths within your own website. 

absolute paths provide the complete website address where you want the user to go.

EXPRESS DOESN'T NEED 'ID'. EXPRESS needs THE 'PARAMETER'


https://mongoosejs.com/docs/api
활용하면서 찾는다.


sort({_id: -1}) => 순서를 앞뒤로 바꾼다. sort by id

*** ESlint ***
CODE STRUCTURE위해서 install 한다.

 npm install eslint 

 npm은 package를 설치한다. => node_modules 
 sometimes you just want to use the package everywhere.
 if you install npm globally, you can use it in other projects.
     
    "npm install eslint -g"
    When you are done installing eslint =>
     "eslint --init"
     "npm install eslint-config-prettier"

    => 추가를 해야한다. (.eslintrc.js)
      extends: ["airbnb-base", "plugin:prettier/recommended"],

    => npm install eslint -D (install locally)
    => npm install prettier -D
    => npm install --save-dev eslint-plugin-prettier
    => npm install --save-dev eslint-config-prettier
    => npm install --save-D eslint-plugin-import

Regular expression은 string으로 부터 무언가를 가지고 온다.
https://regex101.com

https://docs.mongodb.com/manual/reference/operator/query/

***SEARCH***

find title by using regular expression
ex)
$regex: searchingBy
$options: "i" => "i" means insensitive

설명과 제목을 동시에 검색
https://docs.mongodb.com/manual/reference/operator/query/or/ 

    videos = await Video.find({
      $or: [
        { title: { $regex: searchingBy, $options: "i" } },
        { description: { $regex: searchingBy, $options: "i" } }
      ]
    });

middlewares.js 파일에 있는, multerVideo.single("videosFile") 
*upload.pug에 있는 name 동일 해야함!!

    input(type="file", id="file", name="videoFile", required=true, accept="video/*")

WEBPACK is module bundler

많은 파일들을 가져와서, webpack에게 주면, webpack은 static 파일로 변환해준다.(브라우저가 알아들을 수 있드록 해준다.)
file => webpack => file (compatible files) for browser.

***npm install webpack webpack-cli***
***webpack.config.js 파일 생성***  
***
package.json => "scripts" => "start" => "dev:server"변경 
"dev:assets":"" 추가
npm start 대신 npm run dev:server , npm run dev:assets로, 각자 다른 콘솔에서 실행시켜야한다.
when somebody inserts dev:assets, it calls " webpack " => "dev:assets" : "webpack"
webpack will automatically find "webpack.config.js" 

rule: webpack은 exported configuration object를 찾는다.
webpack.config.js file doesn't work with server code 
webpack.config.js file is fully 100% client code
따라서, "babel-node"를 쓸 수가 없다.
"dev:server": "nodemon --exec babel-node init.js --delay 2",
THEREFORE, you need to work old JavaScript on webpack.config.js
ex)
 export / import 대신, modlue.exports = config; 방식으로 코드를 짠다.

WEBPACK has TWO things (entry, output)

 entry: where your file comes from.
 output: where do you want to put it? (output should be an Object)

 *Create a folder called "assets", and then two folders inside "assets" (js, scss)
 
 *NODE.JS에는 파일과 디렉토리(경로)를 absolute로 만들어주는 방법이 있다.
 (컴퓨터나, 서버에서의 전체 경로를 나타낸다.)  
  노드 패키지인 'path'를 사용해서 할 수 있다. 
  const path = require('path'); => webpack can't read the modern JavaScript

 ex) /users/frankkim/documents/youtubeProject/assets

 TO get the path => const ENTRY_FILE = path.resolve(__dirname, "input/your/path" ) 
* __dirname은 현재의 프로젝트 디렉토리 이름이다. 어디서나 접근 가능한 NODE JS 글로벌 변수.

const OUTPUT_DIR = path.join("__dirname", "static") 
OUTPUT_DIR는 file이 아닌, directory다. => "static"이라는 폴더로 export 


path.resolve returns a full path from the root of your computer to the file.
path.resolve creates the absolute path.

path.join joins two paths together.




***
webpack-cli는 터미널에서 webpack을 쓸 수 있게 해준다.

*webpack MODE를 설정해준다.
package.json => "scripts" => 
    
    "dev:assets": "WEBPACK_ENV=development webpack"

*"build:assets"를 추가한다. > 코드를 SERVER에 올려준다.

    "build:assets": "WEBPACK_ENV=production webpack"

*webpack.config.js  에서 package.json에서 생성한 .env파일을(ENV) 불러온다.
const MODE = process.env.WEBPACK_ENV;
process.env."WEBPACK_ENV" === package.json("WEBPACK_ENV") 이름이랑 똑같아야 한다.


WEBPACK은 css파일을 읽지 못해서 설정을 해줘야 한다.
WEBPACK doesn't know anything so we need to add loader. 
we are going to give webpack  "rules"(array)
whenever webpack finds module, we should give webpack rules(array).

webpack은 config 파일에서, 아래에서 위로 실행한다.

        module: {
            rules: [
            {
                test: /\.(scss)$/,
                use: ExtractCSS.extract([ // EXTRACT CSS TEXTS =>
                {
                    loader: "css-loader" // getting the pure CSS
                },
                {
                    loader: "postcss-loader" // make CSS FILES compatible with browsers
                },
                {
                    loader: "sass-loader" // sass => normal CSS
                }
                ])
            }
            ]
        },

    1. regular expression("/\(.scss|sass)$/") will find all the scss, sass files
   
    2. and then it will change them to css files

        npm install --save-dev extract-text-webpack-plugin
        or npm install extract-text-webpack-plugin@next  for beta version

        *const ExtractCSS = require("extract-text-webpack-plugin"); in webpack.config.js
   
    3. extract pure text   
    4. and then make a file only with css files 

    PostCSS는 많은 기능들이 있다. ex) Autoprefixer
    npm install node-sass
    npm install autoprefixer

 dotenv does not create process.env, dotenv is to load the contents of the .env file to the process.env

 There are lots of variables on process.env, dotenv is just a way of adding them.

When do you usually use process.env? 
=> When you want to know if you're developing or on production.

***npm install babel-loader***
what does babel-loader do?

dev:assets "-w"=> (webpack 실행시 => static 폴더로 이동(app.js서버에 설정)
Watch the files because CSS 파일 수정할 때마다, webpack 자동 실행.
That means it is going to watch CSS and run if any updates


    "dev:assets": "WEBPACK_ENV=development webpack -w",

webpack.config 설정이 바뀌면, 다시 dev:assets 이용하여 재실행 시켜야한다.



babel-loader is the Webpack loader responsible for taking in the ES6 code and making it understandable by the browser of choice

***babel polyfill***
npm install @babel/polyfill

gitignore(static)


# \*

# \*

---




-----------------------node 시작-----------------------
npm은 인터넷에서 다운받은 후 설치

npm -v 하면 버전 확인 가능(내 PC에 설치가 되어있는지 버전체크 겸 확인 용으로 좋다)

-----------------------node 끝-----------------------
-----------------------node 서버세팅 시작-----------------------
터미널에서 폴더로 접속 후 npm init 하면 package.json파일이 생성된다. (수정할 부분 수정 한다.)

그 후에 npm install express를 입력하면 서버세팅 완료

package-lock.json 파일과 node_modules폴더가 생성된다.

package-lock.json 파일과 node_modules폴더를 지우더라도

package.json에 "dependencies": { "express": "^4.17.1" }

가 있기 때문에 npm install만 해도 자동으로 package-lock.json 파일과 node_modules폴더가 생성된다.

-----------------------node 서버세팅 끝-----------------------
-----------------------gitignore 시작-----------------------
github에 파일 올릴때는 package-lock.json 파일과 node_modules폴더는 git에 올리면 안되므로 .gitignore를 생성한 후 .gitignore파일 안에 node_modules와 package-lock.json를 타이핑 후 gitignore nodejs검색 사이트 들어가서 그 안에 있는 문자 복사후 .gitignore안에 붙혀넣기 한다.

.gitignore안에 있는 타이핑들은 업로드 안된다.

-----------------------gitignore 끝-----------------------
-----------------------babel 시작-----------------------
ES6를 사용할 수 있게 해주는?? 공식문서 홈페이지 https://babeljs.io/docs/en/

npm install @babel/node 설치해주고 babel은 stage가 많은데 그 중 하나를 골라 설치한다

npm install @babel/preset-env 설치해주고 babel은 맞는 js를 설치해 주어야 한다.

.babelrc파일을 만들고 그 안에 { "presets": ["@babel/preset-env"] }

를 타이핑 한다 (state를 env로 해서 타이핑을 env로 함)

"scripts": { "start": "node index.js" -> "babel-node index.js"로 변경 }

npm install @babel/core 설치

그 후에 더 세련되게 코드 수정

-----------------------babel 끝-----------------------
-----------------------nodemon 시작-----------------------
ps : dependencies는 프로젝트에 필요한 것들, devDependencies는 개발자가 필요한 것들 npm install nodemon -D (-D는 devDependencies로 설정이 된다.)

nodemon은 소스 파일 수정 후 서버를 꼈다 켰다 할 필요 없시 저장만 하면 알아서 새로고침이 된다

(홈페이지에서 따로 새로고침은 해줘야 한다 | vsc에서 live server와는 다름)

"scripts": { "start": "babel-node index.js" -> "start": "nodemon --exec babel-node index.js"로 변경 }

-----------------------nodemon 끝-----------------------
-----------------------Middlewares 시작-----------------------
morgan : 로그 기록을 남기는 모듈 | npm install morgan 후 import한다

helmet : NodeJS 보안을 강화해준다 | npm install helmet 후 import한다

body-parser : POST 요청 데이터를 추출할 수 있도록 만들어 주는 미들웨어 | npm install body-parser 후 import한다

cookie-parser : 요청된 쿠키를 쉽게 추출할 수 있도록 해주는 미들웨어 | npm install cookie-parser 후 import한다

PS. local에 있는 파일은 import할 경우 알파벳 순서로 해주는 것이 좋다 (보기 좋고 찾기 편하다)

-----------------------Middlewares 끝-----------------------
-----------------------router 시작-----------------------
라우팅은 애플리케이션 엔드 포인트(URI)의 정의, 그리고 URI가 클라이언트 요청에 응답하는 방식

페이지가 많아질수록 관리하기 어렵고 복잡해지는데 그 복잡도를 낮추는 방법중 하나이다.

app.js에서 소스 맨 마지막에 export default app;을 하는 이유는 아무개가 프로젝트는 import할 수 있도록 하기 위해서 (react 수업 들을 때 많이 나온 부분)

같이 위치에서 import를 할 경우 ./아무개 이런식으로

default를 import할때는 import app default가 아닌 상태에서 import할때는 import {app}

-----------------------router 끝-----------------------
-----------------------mvc part 1 시작-----------------------
M odel : data V iew : how does the data look C ontroller : function that look for the data

-----------------------mvc part 1 끝-----------------------
-----------------------mvc part 2 시작-----------------------
routers.js에 경로를 모아둔 것은 재사용때문에?? URL전체 구조를 외울 필요성을 줄이기 위해?? router에서 경로 설정을 할 때 /user/:id 이런식으로 :가 붙는 경우는 id 값이 변경이 된다는 뜻이다 /user/id 는 id가 그저 id라는 글자로 인식된다 ../는 현재 경로에서 한 단계 윗 경로로 이동 (현재경로에서 한 단계 바깥경로로 빠져 나간다고 보면 된다.)

-----------------------mvc part 2 끝-----------------------
-----------------------mvc part 3 시작-----------------------
function test() { return something; } 위 아래는 같은 의미 const test() => something;

-----------------------mvc part 3 끝-----------------------
-----------------------pug 시작-----------------------
pug는 HTML을 더 괜찮게 보이도록 만들어준다

npm install pug

views라는 폴더를 만들고 그 안에 .pug파일을 만들어서 사용

Hello
일단 html
h1 Hello pug를 이용한 html

pug는 파이썬처럼 들여쓰기 스타일이다

content는 main이 되는 pug에 block content를 하고 다른 페이지 맨 위에 extents 메인pug를 하면 된다

ex) layouts폴더 안에main.put extents layouts/main

partials은 include로 사용한다 component를 독립시키는 것 조직화 하는 것이 좋다

#{}를 하면 자바스크립트 코드를 사용할 수 있다

-----------------------pug 끝-----------------------
-----------------------fontawesome 시작-----------------------
fontawesome.com 접속 후 고유 스크립트를 신청하면 Kits에 본인 스크립트가 나온다 그것을 html -> head 쪽에 입력하면 된다

-----------------------fontawesome 끝-----------------------
Pages:
Home
Join
Login
Search
User Detail
Edit Profile
Change Password
Upload
Video Detail
Edit Video
Pages:
-----------------------MongoDB 시작-----------------------
MongoDB는 NoSQL이다 https://www.mongodb.com/

https://www.mongodb.com/download-center/community 다운로드 url

version, OS, package를 맞춰서 다운로드 한다

ex(version은 current release가 가장 적합, OS는 사용하는 OS, Package는 윈도우의 경우 zip 말고 msi로) 2019-01-07 기준

다운 받은 후 설치 설치 중간 중간 선택해야 되는 상황에서는 recommand되어 있는 걸로 하는게 좋다

url = MongoDB를 설치하면 보통 C:\Program Files 설치가 되고 MongoDB\Server\4.2\bin까지 접속을 한 후 폴더 url 복사 (4.2는 버전 다를 수 있다) 2020-01-07 기준

환경설정 변수잡기 -> 내 PC - (마우스 오른쪽 클릭)속성 - 고급 시스템 설정 - 환경 변수 - 시스템 변수 - Path - 편집 - 새로 만들기 - url - 확인 후 환경설정 변수를 잡는다

터미널에 mongod를 입력 실행 확인 후 다른 터미널에 mongo를 입력 확인 후 exit

https://mongoosejs.com/ 는 몽고db를 js에서 사용할 수 있게 해주는 것

npm install mongooes 몽고DB를 NodeJS에서 사용하기 위해 install

use wetube (내 데이터베이스 이름 | 본인이 확인하고 싶은 데이터베이스 명을 use + 입력해야한다.)

-----------------------MongoDB 끝-----------------------
-----------------------dotenv 시작-----------------------
npm install dotenv

DB연결시 공유하고 싶지 않은 정보들은 보안유지 해주는?? import dotenv from "dotenv";

dotenv.config();

process.env.MONGO_URL

process는 dotenv를 사용할 때 쓰는 것 같고 env는 .env파일을 의미 .MONGO_URL은 .env안에 있는 변수

.gitignore에 .env가 있어서 github에 업로드는 안된다

-----------------------dotenv 끝-----------------------
-----------------------dotenv 시작-----------------------
npm install dotenv

DB연결시 공유하고 싶지 않은 정보들은 보안유지 해주는?? import dotenv from "dotenv";

dotenv.config();

process.env.MONGO_URL

process는 dotenv를 사용할 때 쓰는 것 같고 env는 .env파일을 의미 .MONGO_URL은 .env안에 있는 변수

.gitignore에 .env가 있어서 github에 업로드는 안된다

-----------------------dotenv 끝-----------------------
-----------------------multer 시작-----------------------
npm install multer

Multer는 파일 업로드를 위해 사용되는 multipart/form-data 를 다루기 위한 node.js 의 미들웨어

효율성을 최대화 하기 위해 busboy 를 기반으로 하고 있다.

(busboy는 나중에 알아보자 | 서버(홀에서 일하는 사람들) 도와주는게 busboy이긴한데 ;;;)

Multer는 multipart (multipart/form-data)가 아닌 폼에서는 동작하지 않습니다.

github에 동영상을 올리 생각이 없으므로 .gitignore에 uploads를 설정

한 개의 서버에서 데이터베이스(특히 파일들)와 UI단??은 다르게 다뤄야 효율이 좋다

-----------------------multer 끝-----------------------
-----------------------eslint 시작-----------------------
eslint는 코드의 에러를 잡아주는 것이라 생각하면 편하다

vscode에서 eslint확장자 설치해주고

npm install eslint -g || -g는 글로벌로 해당 프로젝트 넘은 범위에서 설치가 된다는 의미이다.

(이걸로 설치 ㄴㄴ인줄 알았는데 -g를 해야 eslint --init이 작동한다)

npm install eslint-config-prettier는

vsc에서 prettier이란 소스를 자동으로 변환해주는 확장자를 설치했기 때문에

eslint와 prettier가 맞지 않아서 잡에러를 발생하는 것을 방지하기 위해서

(-D는 프로젝트가 아니라 해당 개발자만 설치하는 방법)

eslint --init 상황에 맞게 클릭 클릭 Yes OR No(어렵네 ㅜㅜ)

npm install eslint-config-airbnb-base -D | npm install eslint-plugin-import -D

npm install eslint-config-prettier -D | npm install eslint-plugin-prettier -D | npm install prettier -D

이 후 eslintrc.js 파일에 extends를 ["airbnb-base", "prettier"]로 변경

rules: { "no-console": "off" } rules에 기능 추가를 할 수 있다

잘을 모르겠으나 완료되면 npm uninstall eslint -g하자

install할것 전부 인스톨 이후 .eslintrc.js 파일 생성후 안에 코드를 직접 입력하는 방식도 있다

-----------------------eslint 끝-----------------------
-----------------------webpack 시작-----------------------
npm install webpack webpack-cli

webpack is working with file webpack-cli working with Terminal

webpack.config.js 파일을 생성한다

package.json에서 scripts쪽 수정한다

start -> dev:server, dev:assets: webpack

npm install cross-env 설치 후 dev:assets WEBPACK앞에 cross-env를 붙혀준다.

npm install extract-text-webpack-plugin@next

@를 붙히면 원하는 버전으로 설치가 가능하다

webpack.config.js에서 loader을 활용하기 위해서

npm install css-loader postcss-loader sass-loader 설치한다

npm install node-sass 설치한다

autoprefixer을 사용하기 위해 npm install autoprefixer

postcss.org나 browserslist에서 document같은 형식의 파일을 본다

npm run dev:assets 지정한 폴더와 파일이 생긴다 (package.json에 설정한 이름을 run한 것임)

npm install babel-loader

npm install @babel/polyfill

dev:assets 끝에 -w는 watch라는 뜻으로 -w하면 다 본다 뭐 이런기능???;;

-----------------------webpack 끝-----------------------
-----------------------PassportJS 시작-----------------------
authentication middleware for Node.js

npm install passport-local-mongoose

npm i passport passport-local

-----------------------PassportJS 끝-----------------------
-----------------------express session 시작-----------------------
npm install express-session

express에서 session을 사용할 수 있게 도와주는

-----------------------express session 끝-----------------------
-----------------------connect-mongo 시작-----------------------
npm install connect-mongo

session에 쿠키는 담는 역학이다

-----------------------connect-mongo 끝-----------------------
-----------------------github Login 시작-----------------------
npm install passport-github

github홈페이지 -> 개발자페이지 application등록 해야한다. (OAuth Apps)

Authorization callback URL이 포인트

생성하면 ID와 PW를 제공하는데 이거는 절대 비밀이다

arg가 순서대로 여러가지가 있을 경우네 순서가 어긋나면 안된다.

function test(1,2,3,4){} | 다만 첫 번째, 두 번째 사용을 안하고 세 번째를 사용하고 싶을 경우

function test(*, \_\_, 3, 4)를 해야지 function test(3,4)하면 에러가 난다 || *가 자동으로 \_로 저장 됌

github email이 public이나 아니냐 때문에 에러가 났다. 각 사이트바다 이메일을 보내는 방식이든

아이디를 통한 로그인 방식이든 application과의 보안 혹은 공유범위에 따라 에러가 날 수도 있다

-----------------------github Login 끝-----------------------
-----------------------facebook 시작-----------------------
npm install passport-facebook

developers.facebook.com에 들어가서 등록해야 한다

application 등록하고 설정으로 들어간다음 Site URL입력 후

설정 -> 기본설정에 들어가서 IP와 SECRET번호를 가져온다

상태 off를 on으로 바꿔준다

Privacy Policy URL에

http://www.paaaportjs.org.packages/paaaport-facebook (passportjs에서 facebook 페이지)

Make App Public 에서 Entertainment(나중에 알오보고)로 설정 후 Confirm

App Review에서 My permissions and Features에서 확인해봅시다

facebook은 http를 안 좋아하고 안 믿어서 https가 필요하다

Facebook Login -> Ssettings -> Valid OAuth Redirect URIs에

ngrok http 4000부터 얻은 URI를 추가 한다

-----------------------facebook 끝-----------------------
-----------------------localtunnel 시작-----------------------
로컬서버에 https 터널을 만들어 준다

npm install -g localtunner

lt --port 4000(4000은 우리가 처음에 설정한 번호)를 입력하면

새로운 URL을 준다

package.json에서 "tunnel": "lt -- port 4000"추가 (2020-10-20)에서 너무 오래걸리거나 안되어서

npm install -g ngrok설치 후 ngrok http 4000으로 하니까 됌

-----------------------localtunnel 끝-----------------------
