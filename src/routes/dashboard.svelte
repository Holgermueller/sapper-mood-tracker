<script>
  import TodaysDate from "../dashcomponents/TodaysDate.svelte";
  import MoodRange from "../dashcomponents/MoodRange.svelte";
  import InstancesTracked from "../dashcomponents/InstancesTracked.svelte";
  import Graph from "../dashcomponents/Graphs.svelte";
</script>

<svelte:head>
  <title>Dashboard</title>
</svelte:head>

<TodaysDate />
<MoodRange />
<InstancesTracked />
<Graph />
