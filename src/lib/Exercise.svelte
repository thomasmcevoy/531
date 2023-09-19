<script>
  import Workout from "./Workout.svelte";

  export let exercise, weekNumber, settings;
</script>

<div class="exercise">
  <div class="header">
    <h3>{exercise.name}</h3>
    {#if weekNumber === 0}
      <h4 class="training-max-container">
        <input
          type="text"
          class="training-max"
          bind:value={exercise.trainingMax}
        />
      </h4>
    {:else}
      <div class="training-max-placeholder" />
    {/if}
  </div>

  <Workout {settings} {weekNumber} trainingMax={exercise.trainingMax} />
</div>

<style>
  @media (min-width: 850px) {
    .exercise {
      height: 11.5em;
    }
  }

  .header {
    width: 33.33%;
    text-transform: capitalize;
  }

  .training-max-container {
    text-align: right;
  }
  .training-max,
  .training-max-placeholder {
    border: none;
    height: 1.33rem;
    width: 2rem;
    text-align: center;
  }
  .training-max {
    background: #eee;
    touch-action: manipulation;
  }
</style>
