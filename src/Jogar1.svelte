<script>
	import VoltarMenu from "./VoltarMenu.svelte";
	let tabela = [
		"images/65.png",
		"images/64.png",
		"images/63.png",
		"images/62.png",
		"images/61.png",
		"images/60.png",
		"images/59.png",
		"images/58.png",
		"images/57.png",
		"images/56.png",
		"images/55.png",
		"images/54.png",
		"images/53.png",
		"images/52.png",
		"images/51.png",
		"images/50.png",
	];

	let tabelaCerta = [
		"images/65.png",
		"images/64.png",
		"images/63.png",
		"images/62.png",
		"images/61.png",
		"images/60.png",
		"images/59.png",
		"images/58.png",
		"images/57.png",
		"images/56.png",
		"images/55.png",
		"images/54.png",
		"images/53.png",
		"images/52.png",
		"images/51.png",
		"images/50.png",
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
	<link rel="stylesheet" href="/styles/jogar1.css" />
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
