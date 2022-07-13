<script>
	import Jogo from './Dificuldades.svelte'
	import Sobre from './Sobre.svelte'
	import Menu from './Menu.svelte'
	import Ajuda from './Ajuda.svelte'
	import Jogar from './Jogar.svelte'
	import Jogar1 from './Jogar1.svelte'
	import Jogar2 from './Jogar2.svelte'
	import { estado } from './Estado.js'
</script>

{#if $estado === 'menu'}
	<Menu/>
{:else if $estado === 'sobre'}
	<Sobre/>
{:else if $estado === 'jogar'}
	<Jogo/>
	{:else if $estado === 'ajuda'}
	<Ajuda/>
	{:else if $estado === 'Jogar'}
	<Jogar/>
	{:else if $estado === 'Jogar1'}
	<Jogar1/>
	{:else if $estado === 'Jogar2'}
	<Jogar2/>
{/if}