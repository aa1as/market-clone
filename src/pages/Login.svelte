<script>
  import { getAuth, signInWithPopup, GoogleAuthProvider } from "firebase/auth";
  import { user$ } from "../store";
  const provider = new GoogleAuthProvider();
  const auth = getAuth();

  const loginWithGoogle = async () => {
    try {
      const result = await signInWithPopup(auth, provider);
      const credential = GoogleAuthProvider.credentialFromResult(result);
      const token = credential.accessToken;
      const user = result.user;
      user$.set(user);
      localStorage.setItem("token", token);
    } catch (error) {
      console.error(error);
    }
  };
</script>

<div>
  {#if $user$}
    <div>{$user$.displayName}로그인됨</div>
  {/if}
  <div>로그인하기</div>
  <button class="login-btn" on:click={loginWithGoogle}>
    <img
      class="google-img"
      src="https://www.google.com/imgres?q=%EA%B5%AC%EA%B8%80%EB%A7%88%ED%81%AC&imgurl=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHDY7T%2FbtrY2our4Rw%2FFw6bz0QroBUp1YxglkkwEK%2Fimg.webp&imgrefurl=https%3A%2F%2Fdesignlog.org%2F2513060&docid=9yNGC7pTXIRW_M&tbnid=0l_BJeH_qEpbzM&vet=12ahUKEwiO_tXShYOGAxVojVYBHQhhCYEQM3oECBoQAA..i&w=1000&h=563&hcb=2&ved=2ahUKEwiO_tXShYOGAxVojVYBHQhhCYEQM3oECBoQAA"
      alt=""
    />
    <div>Google로 시작하기</div>
    <div />
  </button>
</div>

<style>
  .login-btn {
    width: 200px;
    height: 50px;
    border: 1px solid gray;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    border-radius: 3px;
  }

  .google-img {
    width: 20px;
  }
</style>
