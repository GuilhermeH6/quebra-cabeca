<svelte:head>
	<link rel="stylesheet" href="/styles/menu.css">
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
</svelte:head>

<script>
	import { estado } from './Estado.js'
	import { trocarEstadoDoJogo } from './Estado.js'
	import VoltarMenu from "./VoltarMenu.svelte";
	const menuAudio = new Audio('sounds/audioHover.wav');
	const menuPlay = new Audio('sounds/audioClick.wav');

	function handleMouseover() {
		menuAudio.pause();
		menuAudio.currentTime = 0;
		menuAudio.play();
	}

	function handlePlayGame() {
		menuPlay.pause();
		menuPlay.currentTime = 0;
		menuPlay.play();
	}
</script>

<br>
<br>
<br>
<br>

<h1>
	ESCOLHA SEU NIVEL
</h1>
<br>
<br>
<br>
<br>
<br>
<br>
<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div  class='menu' on:mouseover={handleMouseover} on:click={handlePlayGame} on:click={() => trocarEstadoDoJogo('Jogar')}>
    EASY
</div>

<br>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div class='menu' on:mouseover={handleMouseover} on:click={handlePlayGame} on:click={() => trocarEstadoDoJogo('Jogar1')}>
	MEDIUM
</div>

<br>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div class='menu' on:mouseover={handleMouseover} on:click={handlePlayGame} on:click={() => trocarEstadoDoJogo('Jogar2')}>
	HARD
</div>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<VoltarMenu />