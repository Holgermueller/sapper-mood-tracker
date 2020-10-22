<script>
  import { MoodStore } from "../stores/MoodStore";
  $: daysTracked = $MoodStore.reduce((a, { timesFelt }) => a + timesFelt, 0);
</script>

<style>
  h3 {
    margin: 0 auto;
    color: #555;
    text-align: center;
  }
  p {
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
    text-align: center;
  }
</style>

<h3>How often you feel each mood.</h3>

<p>Total days tracked: {daysTracked}</p>
