<form id="signup-form" action="/signup" method="POST">
  <div>회원가입</div>
  <div>
    <lable for="id">아이디</lable>
    <input type="text" id="id" name="id" required />
  </div>
  <div>
    <lable for="password">패스워드</lable>
    <input type="password" id="password" name="password" required />
  </div>
  <div>
    <lable for="password2">패스워드 확인</lable>
    <input type="password" id="password2" name="password2" required />
  </div>
  <div>
    <lable for="name">이름</lable>
    <input type="text" id="name" name="name" required />
  </div>
  <div>
    <lable for="email">이메일</lable>
    <input type="email" id="email" name="email" required />
  </div>
  <div>
    <button type="submit">회원 가입하기</button>
  </div>
  <div id="info"></div>
</form>
