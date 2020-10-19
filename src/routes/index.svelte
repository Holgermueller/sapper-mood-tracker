<script>
  import Tabs from "../shared/Tabs.svelte";
  import Registration from "../LoginRegistration/Registration.svelte";
  import Login from "../LoginRegistration/Login.svelte";

  let items = ["Registration", "Login"];

  let activeItem = "Registration";
  const tabChange = (e) => (activeItem = e.detail);

  const handleAdd = () => {
    activeItem = "Login";
  };
</script>

<style>
  h1,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>

<svelte:head>
  <title>Mood Tracker</title>
</svelte:head>

<h1>Welcome to the Mood Tracker!</h1>

<p><strong>Keep track of your mood swings here!!</strong></p>

<Tabs {activeItem} {items} on:tabChange={tabChange} />
{#if activeItem === 'Registration'}
  <Registration />
{:else if activeItem === 'Login'}
  <Login />
{/if}
