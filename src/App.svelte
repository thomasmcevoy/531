<script>
  import { onMount, onDestroy } from "svelte";
  import Exercise from "./lib/Exercise.svelte";
  import Settings from "./lib/Settings.svelte";

  export const weeks = ["I", "II", "III", "IV"];

  export let settings = {
    increment: 5,
    foreverDeload: true,
  };

  export let exercises = [
    { name: "front squat", trainingMax: 130, isVisible: true },
    { name: "bench", trainingMax: 140, isVisible: true },
    { name: "deadlift", trainingMax: 235, isVisible: true },
    { name: "press", trainingMax: 100, isVisible: false },
  ];

  onMount(async () => {
    // squat = await localStorage.getItem('squat') || squat;
    // bench = await localStorage.getItem('bench') || bench;
    // deadlift = await localStorage.getItem('deadlift') || deadlift;
  });

  onDestroy(() => {
    // localStorage.setItem('squat', squat);
    // localStorage.setItem('bench', bench);
    // localStorage.setItem('deadlift', deadlift);
  });
</script>

<div id="page">
  <Settings {settings} bind:exercises />
  {#each weeks as week, i}
    <div class="week">
      <h2>Week {week}</h2>
      {#each exercises as exercise}
        {#if exercise.isVisible === true}
          <Exercise bind:exercise weekNumber={i} {settings} />
        {/if}
      {/each}
    </div>
  {/each}
</div>

<style>
  #page {
    width: 100%;
    margin: 0;
    border: 6px var(--font-color) double;
    padding-bottom: 2vw;
    padding-left: 3vw;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    font: var(--font-size) / 1 helvetica;
    overflow: hidden;
  }
  @media (min-width: 450px) {
    #page {
      padding-left: 0.75em;
      font-size: var(--font-size-wide);
    }
  }
  @media (min-width: 850px) {
    #page {
      height: 100vh;
      padding-left: 0.33em;
    }
  }

  .week {
    padding-top: 0.667em;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  @media (min-width: 450px) {
    .week {
      width: 50%;
    }
  }
  @media (min-width: 850px) {
    .week {
      padding-top: 0.4em;
      width: 25%;
    }
  }
</style>
