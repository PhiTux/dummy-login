<script>
  import { username, password } from '$lib/store.js';
  import { goto } from '$app/navigation';
  import { slide } from 'svelte/transition';

  function goToLogin() {
    $username = "";
    $password = "";
    goto('/');
  }

  let showCredentials = $state(false);
</script>

<div class="explanation">
  <h1>Du bist nun eingeloggt!</h1>

  Leider gibt es hier nichts zu sehen, weil es eben nur ein Dummy Login ist.<br> <br>
  Aber du kannst dir deine eingegebenen Daten anzeigen lassen, die du gerade <u>an den Server gesendet</u> hast.<br>
</div>

<div class="showData">
  <input id="showCredentials" type="checkbox" bind:checked={showCredentials}>
  <label for="showCredentials">Zeige meine Login Daten</label>

  {#if showCredentials}
    <div class="credentials" transition:slide>
      Username: <b>{$username}</b><br>
      Passwort: <b>{$password}</b>
    </div>
  {/if}
</div>

<button onclick={() => (goToLogin())}>
  Zurück zum Login
</button>


<style>
  .showData {
    background-color: #f0f0f0;
    padding: 20px;
    border-radius: 10px;
    font-size: 1.1em;
  }

  .credentials {
    background-color: #c7c7c7;
    padding: 10px;
    border-radius: 5px;
    margin-top: 10px;
    font-size: 1.2em;
  }

  button {
    margin-top: 10px;
    padding: 10px 20px;
    font-size: 1em;
    background-color: #e48a37;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
</style>