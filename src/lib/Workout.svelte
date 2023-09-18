<script>
  export let weekNumber,
    trainingMax,
    increment = 5,
    sets,
    foreverDeload;

  export function round(n) {
    if (!isNaN(n)) return Math.round(n / increment) * increment;
    return 0;
  }
</script>

<div class="workout">
  <div class="reps column">
    <div class="column-title">Reps</div>
    <div class="reps-container">
      <div class="reps">{weekNumber === 1 ? 3 : 5}</div>
      <div class="reps">{weekNumber === 0 ? 5 : 3}</div>
      <div class="reps">
        {weekNumber === 0 ? 5 : weekNumber === 1 ? 3 : 1}{weekNumber !== 3
          ? "+"
          : ""}
      </div>
      {#if foreverDeload && weekNumber === 3}
        <div class="reps">1</div>
      {/if}
    </div>
  </div>

  <div class="weight column">
    <div class="column-title">Weight</div>
    {#each sets as set, i}
      <div class="weight">{round(trainingMax * set[weekNumber])}</div>
    {/each}
    {#if foreverDeload && weekNumber === 3}
      <div class="weight">{trainingMax}</div>
    {/if}
  </div>
</div>

<style>
  .workout {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
  }

  .column {
    text-align: right;
  }

  .column-title {
    padding: var(--small-padding) 0;
    font-style: italic;
  }
  .column:first-child .column-title {
    text-align: left;
  }

  .reps,
  .weight,
  .column {
    padding: var(--small-padding) 0;
  }

  .reps-container {
    float: right;
  }

  .reps {
    text-align: left;
  }
</style>
