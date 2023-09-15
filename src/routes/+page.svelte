<script>
	import { onMount, onDestroy } from 'svelte';
	import Exercise from './exercise.svelte';

	export let exercises = [
		{ name: 'squat', trainingMax: 130, isVisible: true },
		{ name: 'bench', trainingMax: 140, isVisible: true },
		{ name: 'deadlift', trainingMax: 235, isVisible: true },
		{ name: 'press', trainingMax: 100, isVisible: true }
	];

	export const weeks = ['I', 'II', 'III', 'IV'];

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
	{#each weeks as week, i}
		<div class="week">
			<h2>Week {week}</h2>
			{#each exercises as exercise}
				{#if exercise.isVisible === true}
					<Exercise bind:exercise weekNumber={i} />
				{/if}
			{/each}
		</div>
	{/each}
</div>

<style>
	:global(*) {
		box-sizing: border-box;
	}

	:global(:root) {
		--font-size: 4vw;
		--font-size-wide: calc(0.5rem + 0.5vw);
		--font-color: #222;
		--small-padding: 0.5vh;
	}

	:global(body) {
		margin: 0;
	}

	:global(h2),
	:global(h3),
	:global(h4),
	:global(input) {
		height: 1.25rem;
		margin: 0;
		padding: var(--small-padding) 0;
		font: inherit;
		font-weight: bold;
	}

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
	@media (min-width: 414px) {
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
	@media (min-width: 414px) {
		.week {
			margin-top: 0;
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
