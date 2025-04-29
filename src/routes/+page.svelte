<script>
  import { username, password } from '$lib/store.js';
  import { goto } from '$app/navigation';

  function handleSubmit() {
    fetch('/login', {
			method: 'POST',
			body: JSON.stringify({ username: $username, password: $password }),
			headers: {
				'Content-Type': 'application/json'
			}
		}).finally(() => {
      goto('/success');
    });
  }
</script>

<div class="explanation">
  <h1>Dummy Login</h1>
  Das ist ein "Dummy Login" (Fake Login) nur zu Demonstrationszwecken.<br>
  Jede eingegebene Kombination aus Username & Passwort führt zu einem "erfolgreichen Login".

  <div class="warning">Gib hier <u>niemals echte Passwörter</u> oder Nutzernamen ein!</div>
</div>

<div class="login">
  <h2>Login</h2>
<form on:submit|preventDefault={handleSubmit}>
  <div>
    <label for="username">Username:</label>
    <input type="text" id="username" bind:value={$username} required />
  </div>
  <div>
    <label for="password">Passwort:</label>
    <input type="password" id="password" bind:value={$password} required />
  </div>
  <button type="submit">Login</button>
</form>
</div>

<style>
  button {
    margin-top: 10px;
    padding: 10px 20px;
    font-size: 1em;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  :global(body) {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: sans-serif;
  }

  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  form > div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    margin-bottom: 10px;
  }

  input {
    margin-left: 10px;
    font-size: 1em;
  }

  .login {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 300px;
    margin-top: 20px;
    padding: 20px;
    border-radius: 10px;
    background-color: #84c78ea3;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }

  :global(.explanation) {
    margin-bottom: 20px;
    text-align: center;
    background-color: #8edcff;
    padding: 20px;
    border-radius: 10px;
    font-size: 1.1em;
  }

  .warning {
    margin-top: 10px;
    color: rgb(227, 21, 21);
    font-weight: bold;
    font-size: 1.2em;
  }
</style>