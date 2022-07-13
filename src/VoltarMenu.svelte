<script>
	import { trocarEstadoDoJogo } from './Estado.js'

	const menuAudio = new Audio('sounds/audioHover.wav');

	function handleMouseover() {
		menuAudio.pause();
		menuAudio.currentTime = 0;
		menuAudio.play();
	}
</script>

<!-- svelte-ignore a11y-mouse-events-have-key-events -->
<div class='menu' on:mouseover={handleMouseover} on:click={() => trocarEstadoDoJogo('menu')}>
	<h4>VOLTAR AO MENU</h4>
</div>