<script>
  import { MoodStore } from "../../stores/MoodStore";

  const addTodaysMood = (e) => {
    MoodStore.update((moods) => {
      let moodsToUpdate = [...moods];
      let updatedMood = moodsToUpdate.find((mood) => mood.id == e.target.id);
      if (e.target.id === e.target.value) {
        updatedMood.timesFelt++;
      }
      return moodsToUpdate;
    });
  };
</script>

<style>
  h2 {
    margin: 8px auto;
  }
  fieldset {
    width: 55%;
    margin: 8px auto;
    border-radius: 15px;
  }
  button {
    margin: 4px;
    border-radius: 7px;
    width: 15%;
  }
</style>

<h2>Hello, [username]</h2>

<fieldset>
  <legend>
    <h3>How are you feeling today?</h3>
  </legend>

  {#each $MoodStore as mood}
    <button
      on:click={addTodaysMood}
      class="button"
      style="background-color:{mood.color}; border: 1px solid {mood.borderColor}"
      id={mood.id}
      value={mood.id}>
      {mood.mood}
    </button>
  {/each}
</fieldset>
