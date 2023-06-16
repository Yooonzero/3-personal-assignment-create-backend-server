# 3-personal-assignment-create-backend-server

3. Node.js 와 Express로 로그인 기능이 없는 나만의 백엔드 서버 만들기

게시글은 {_id, user, password, title, content, createdAt} 이라는 키값을 가집니다.

{

게시글 생성 : 

body란에 {user, password, title, content}를 작성해 주시면 됩니다.

body의 4개 key들은 각 각 schema에서 required는 true값을 가집니다.

createdAt 은 현재시간을 반영해 자동으로 데이터가 저장됩니다.

_id 값은 몽고db에서 자동으로 저장해줍니다.


게시글 생성 오류메시지 :

res.status(400) : 각 key값들의 value가 하나라도 빈 문자열이라면, "데이터 형식이 올바르지 않습니다"라는 메시지가 출력됩니다. (현재 기능 구현 후 서버 접속 종료가 되는 오류 수정 중)

},


{

게시글 조회 :

http://13.125.59.49:3050/api/posts 로 들어가면 해당 URI의 데이터 베이스에 저장된 데이터의 값이 시간내림차순으로 정렬되어있습니다.

},


{

게시글 상세 조회 :

http://13.125.59.49:3050/api/posts/:{ 조회하고 싶은 게시글에 해당하는 _id값을 넣어줍니다.}

예시 _id : 648be0b09b723ea90071d228


게시글 상세 조회 오류 메시지 :

req.params에 해당하는 _id값을 vlaue로 가지는 게시글이 없다면 res.status(400)에, "데이터 형식이 올바르지 않습니다"라는 메시지가 출력됩니다.

},

{

게시글 수정 :

http://13.125.59.49:3050/api/posts/:{ 수정하고자 하는 게시글에 해당하는 _id값을 넣어줍니다.}

수정은 req.params에 입력하신 _id값을 가지는 게시글의 password와 body에 작성하는 password의 값이 동일할때에만 수정기능이 실행됩니다.

{user,title,content} 값을 body에 작성한 내용대로 수정이 가능합니다.


게시글 수정 오류 메시지 :

user,password,title,content의 값중 하나라도 빈 문자열이 생기거나, password가 일치하지 않다면,

res.status(400)의 "데이터 형식이 올바르지 않습니다"라는 메시지가 출력됩니다.

URI의 _id값이 올바르지 못하다면 res.status(404)의 "해당 게시글이 존재하지 않습니다"라는 메시지가 출력됩니다.

},


{

게시글 삭제 :

http://13.125.59.49:3050/api/posts/:{ 삭제하고자 하는 게시글에 해당하는 _id값을 넣어줍니다.}

body에는 password값만 들어갑니다. URI의 _id값이 가지는 password와 body의 password가 일치해야 삭제로직이 실행됩니다.


게시글 삭제 오류 메시지 :

res.status(400) : password값이 일치하지 않다면, "데이터 형식이 올바르지 않습니다"라는 메시지가 출력됩니다.

res.status(404) : _id값에 해당하는 게시글이 없는경우 "해당 게시글이 존재하지 않습니다"라는 메시지가 출력됩니다. (현재 try~catch 구문에서 catch에 오류가 잡히지 않는 오류 수정 중)

},


{

