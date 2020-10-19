<script>
  import { User } from "../../stores/UsersStore";
  let username = "";
  let password = "";
  let error = "";
  let success = "";

  const validateForm = () => {
    if (!username) {
      error = "You must provide a username.";
    } else if (!password) {
      error = "You must provide a password";
    } else {
      loginUser();
      clearForm();
    }
  };

  const loginUser = () => {
    let userData = {
      username,
      password,
    };
    User.set(userData);
    error = "";
    success = "You are now logged in!";
    return $User;
  };

  const clearForm = () => {
    username = "";
    password = "";
  };
</script>

<style>
  fieldset {
    width: 75%;
    margin: auto;
    border-radius: 8px;
  }
  .input {
    width: 100%;
    border: none;
    border-bottom: 1px solid black;
    margin: 8px auto;
  }
  .error {
    color: red;
  }
  .success {
    color: green;
  }
  .clear {
    border-color: red;
    background-color: red;
    color: white;
    border-radius: 8px;
  }
  .submit {
    background-color: green;
    border-color: green;
    color: white;
    border-radius: 8px;
  }
  .submit:disabled {
    border-color: grey;
    background-color: grey;
  }
</style>

<fieldset>
  <legend>
    <h1>Login Here:</h1>
  </legend>

  <form class="form" id="form" on:submit|preventDefault={validateForm}>
    <input
      class="input"
      type="text"
      name="username"
      id="username"
      bind:value={username}
      placeholder="Username" />
    <input
      class="input"
      type="text"
      name="password"
      id="password"
      bind:value={password}
      placeholder="Password" />

    {#if error}
      <p class="error">{error}</p>
    {/if}

    {#if success}
      <p>Welcome {$User.username}!</p>
      <p class="success">{success}</p>
    {/if}

    <button id="clear" class="clear" on:click={clearForm}>Clear</button>
    <button
      id="submit"
      class="submit"
      disabled={!username || !password}>Submit</button>
  </form>
</fieldset>
