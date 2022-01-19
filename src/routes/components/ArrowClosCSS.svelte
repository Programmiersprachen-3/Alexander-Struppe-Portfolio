<!-- <button class="arrow-button" aria-label="Menu">
	<span class="arrow-icon" />
</button>

<style>
</style> -->
<script>
	import { tweened } from 'svelte/motion';
	import { cubicInOut } from 'svelte/easing';
	import polymorph from 'polymorph-js';
	const interpolate = polymorph.interpolate;

	const progress = tweened(0, {
		duration: 400,
		easing: cubicInOut
	});

	const pausePaths = [
		'M0.5 7.26704C0.5 6.71476 0.947715 6.26704 1.5 6.26704H19.5C20.0523 6.26704 20.5 6.71476 20.5 7.26704C20.5 7.81933 20.0523 8.26704 19.5 8.26704H1.5C0.947716 8.26704 0.5 7.81933 0.5 7.26704Z',
		'M13.1407 13.631C12.7502 13.2405 12.7502 12.6073 13.1407 12.2168L18.7976 6.55994C19.1881 6.16942 19.8212 6.16942 20.2118 6.55994C20.6023 6.95047 20.6023 7.58363 20.2118 7.97416L14.5549 13.631C14.1644 14.0215 13.5312 14.0215 13.1407 13.631Z',
		'M13.1408 0.903075C13.5313 0.512551 14.1645 0.512551 14.555 0.903075L20.2119 6.55993C20.6024 6.95045 20.6024 7.58362 20.2119 7.97414C19.8213 8.36467 19.1882 8.36467 18.7976 7.97414L13.1408 2.31729C12.7503 1.92676 12.7503 1.2936 13.1408 0.903075Z'
	];
	const playPaths = [
		'M1.23466 15.3381C0.84414 14.9476 0.84414 14.3144 1.23466 13.9239L13.9626 1.19598C14.3531 0.805459 14.9863 0.805459 15.3768 1.19598V1.19598C15.7673 1.58651 15.7673 2.21967 15.3768 2.6102L2.64888 15.3381C2.25835 15.7286 1.62519 15.7286 1.23466 15.3381V15.3381Z',
		'M8.03313 8.26703C8.42365 7.8765 9.05682 7.8765 9.44734 8.26703L15.1042 13.9239C15.4947 14.3144 15.4947 14.9476 15.1042 15.3381V15.3381C14.7137 15.7286 14.0805 15.7286 13.69 15.3381L8.03313 9.68124C7.6426 9.29072 7.6426 8.65755 8.03313 8.26703V8.26703Z',
		'M0.961991 1.19598C1.35252 0.805459 1.98568 0.805459 2.3762 1.19598L8.03306 6.85284C8.42358 7.24336 8.42358 7.87653 8.03306 8.26705V8.26705C7.64253 8.65758 7.00937 8.65758 6.61885 8.26705L0.961991 2.6102C0.571467 2.21967 0.571467 1.58651 0.961991 1.19598V1.19598Z'
	];

	const d1 = interpolate([pausePaths[0], playPaths[0]]);
	const d2 = interpolate([pausePaths[1], playPaths[1]]);
	const d3 = interpolate([pausePaths[2], playPaths[2]]);

	let targetProgress = 0;
	function onToggle() {
		targetProgress = 1 - targetProgress;
		progress.set(targetProgress);
	}
</script>

<main>
	<div class="button-background" on:click={onToggle}>
		<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 21 15" fill="none">
			<g transform="translate(0,0)">
				<path d={d1($progress)} />
				<path d={d2($progress)} />
				<path d={d3($progress)} />
			</g>
		</svg>
	</div>
</main>

<style>
	:global(body) {
		display: left;
		align-items: center;
		justify-content: left;
	}

	.button-background {
		width: 70px;
		height: 70px;
		border-radius: 20%;
		background-color: rgb(134, 56, 201);
		display: flex;
		align-items: center;
		justify-content: center;
	}

	path {
		opacity: 1;
		fill: #ffffff;
		fill-opacity: 1;
		stroke: #ffffff;
		stroke-width: 2;
	}
</style>
