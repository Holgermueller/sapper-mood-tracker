<script>
  import { MoodStore } from "../../stores/MoodStore";
  $: instancesTracked = $MoodStore.reduce(
    (a, { timesFelt }) => a + timesFelt,
    0
  );
</script>

<style>
  .graphs {
    width: 75%;
    margin: 0 auto;
  }
  .mood {
    background: #fafafa;
    margin: 10px auto;
    position: relative;
  }
  .single-mood {
    height: 100%;
    position: absolute;
    box-sizing: border-box;
  }
  span {
    text-align: center;
    display: inline-block;
    padding: 10px 20px;
  }
</style>

<div class="graphs">
  {#each $MoodStore as mood}
    <div class="mood">
      <div
        class="single-mood {mood.mood}"
        style="width: {Math.floor((100 / instancesTracked) * mood.timesFelt) || 0}%; background: {mood.color}; border-left: 4px solid {mood.borderColor}" />
      <span>{mood.mood} | Days felt: {mood.timesFelt}</span>
    </div>
  {/each}
</div>
