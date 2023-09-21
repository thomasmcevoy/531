<script>
  export let settings, weekNumber, trainingMax;

  export const sets = settings.foreverDeload
    ? [
        [0.65, 0.7, 0.75, 0.7],
        [0.75, 0.8, 0.85, 0.8],
        [0.85, 0.9, 0.95, 0.9],
      ]
    : [
        [0.65, 0.7, 0.75, 0.4],
        [0.75, 0.8, 0.85, 0.5],
        [0.85, 0.9, 0.95, 0.6],
      ];

  export const reps = [
    [5, 3, 5, 5],
    [5, 3, 3, 3],
    ["5+", "3+", "1+", 1],
  ];

  export function round(n) {
    if (!isNaN(n))
      return Math.round(n / settings.increment) * settings.increment;
    return 0;
  }
</script>

<div class="workout">
  <div class="reps column">
    <div class="column-title">Reps</div>

    <div class="reps-container">
      {#each reps as rep, i}
        <div class="reps">{reps[i][weekNumber]}</div>
      {/each}
      {#if settings.foreverDeload}
        {#if weekNumber === 3}
          <div class="reps">1</div>
        {:else}
          <div class="reps-placeholder" />
        {/if}
      {/if}
    </div>
  </div>

  <div class="weight column">
    <div class="column-title">Weight</div>
    {#each sets as set, i}
      <div class="weight">{round(trainingMax * set[weekNumber])}</div>
    {/each}
    {#if settings.foreverDeload && weekNumber === 3}
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

  .reps,
  .reps-placeholder {
    text-align: left;
    height: 1.5em;
  }
</style>
