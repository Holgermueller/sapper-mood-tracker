<script>
  import { User } from "../../stores/UsersStore";
  let username = "";
  let password = "";
  let confirmPassword = "";
  let error = "";
  let success = "";

  const registerUser = () => {
    let userData = {
      username,
      password,
      confirmPassword,
    };
    User.set(userData);
    error = "";
    success = "You are now registered!";
    return $User;
  };

  const checkUsername = () => {};

  const validateRegistrationForm = (e) => {
    if (!username) {
      error = "You must provide a username!";
    } else if (!password) {
      error = "You must provide a password!";
    } else if (!confirmPassword) {
      error = "You must confirm your password!";
    } else if (password !== confirmPassword) {
      error = "Passwords do not match!";
    } else {
      registerUser();
      clearForm();
    }
  };

  const clearForm = () => {
    username = "";
    password = "";
    confirmPassword = "";
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
  .hint {
    color: lightslategrey;
  }
  .buttons {
    margin-top: 8px;
  }
  .error {
    color: red;
    text-align: center;
  }
  .success {
    color: green;
    text-align: center;
  }
  .clear {
    border-color: red;
    background-color: red;
    color: white;
    border-radius: 8px;
  }
  .submit {
    border-color: green;
    background-color: green;
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
    <h1>Register Here:</h1>
  </legend>

  <form
    class="form"
    id="form"
    on:submit|preventDefault={validateRegistrationForm}>
    <input
      class="input"
      type="text"
      name="username"
      id="username"
      bind:value={username}
      placeholder="Username" />
    <label for="username">
      <small class="hint">(Username must be at least 8 characters long and
        contain one number and one special character.)</small></label>
    <input
      class="input"
      type="text"
      name="password"
      id="password"
      bind:value={password}
      placeholder="Password" />
    <label for="password">
      <small class="hint">(Password must be at least 8 characters long and
        contain one number and one special character.)</small></label>
    <input
      class="input"
      type="text"
      name="confirmPassword"
      id="confirmPassword"
      bind:value={confirmPassword}
      placeholder="Confirm Password" />

    {#if error}
      <p class="error">{error}</p>
    {/if}

    {#if success}
      <p class="success">Welcome {$User.username}!</p>
      <p class="success">{success}</p>
    {/if}

    <div class="buttons">
      <button id="clear" class="input clear" on:click={clearForm}>Clear</button>
      <button
        id="submit"
        class="input submit"
        disabled={!username || !password || !confirmPassword}>Submit</button>
    </div>
  </form>
</fieldset>
