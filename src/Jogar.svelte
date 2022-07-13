<script>
	import VoltarMenu from "./VoltarMenu.svelte";

	let tabela = [
		"images/9.png",
		"images/8.png",
		"images/7.png",
		"images/6.png",
		"images/5.png",
		"images/4.png",
		"images/3.png",
		"images/2.png",
		"images/1.png",
	];

	let tabelaCerta = [
		"images/9.png",
		"images/8.png",
		"images/7.png",
		"images/6.png",
		"images/5.png",
		"images/4.png",
		"images/3.png",
		"images/2.png",
		"images/1.png",
	];

	let pecas = embaralharPecas();

	let click = {
		index: null,
		valor: null,
	};

	function embaralharPecas() {
		let copiaTabela = [].concat(tabela);
		copiaTabela.sort(function () {
			return 0.5 - Math.random();
		});
		let pecas = copiaTabela;
		return pecas;
	}

	function moverPeca(valor, index) {
		if (click.valor === null) {
			click.valor = valor;
			click.index = index;
			return;
		}
		pecas[click.index] = valor;
		pecas[index] = click.valor;
		click.valor = null;
		pecas = [...pecas];
		ganhou(pecas, tabelaCerta);
	}

	function ganhou(pecas, tabelaCerta) {
		let a = pecas.toString();
		let b = tabelaCerta.toString();

		if (a === b) {
			return alert("voce ganhou!!");
		}
	}
</script>

<svelte:head>
	<link rel="stylesheet" href="/styles/jogar.css" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<h1 style="margin-top: 60px;">MONTE SEU QUEBRA-CABEÇA</h1>

<section>
	<ul class="quebraCabeca">
		{#each pecas as peca, i (peca)}
			<li class="peca" on:click={() => moverPeca(peca, i)}>
				<img src={peca} alt="peça" width="100%" height="100%" />
			</li>
		{/each}
	</ul>
</section>

<VoltarMenu />
