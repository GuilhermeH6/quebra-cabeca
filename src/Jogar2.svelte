<script>
	import VoltarMenu from "./VoltarMenu.svelte";

	let tabela = [

		"images/90.png",
		"images/89.png",
		"images/88.png",
		"images/87.png",
		"images/86.png",
		"images/85.png",
		"images/84.png",
		"images/83.png",
		"images/82.png",
		"images/81.png",
		"images/80.png",
		"images/79.png",
		"images/78.png",
		"images/77.png",
		"images/76.png",
		"images/75.png",
		"images/74.png",
		"images/73.png",
		"images/72.png",
		"images/71.png",
		"images/70.png",
		"images/69.png",
		"images/68.png",
		"images/92.png",
		"images/91.png",
	];

	let tabelaCerta =[
		
		"images/90.png",
		"images/89.png",
		"images/88.png",
		"images/87.png",
		"images/86.png",
		"images/85.png",
		"images/84.png",
		"images/83.png",
		"images/82.png",
		"images/81.png",
		"images/80.png",
		"images/79.png",
		"images/78.png",
		"images/77.png",
		"images/76.png",
		"images/75.png",
		"images/74.png",
		"images/73.png",
		"images/72.png",
		"images/71.png",
		"images/70.png",
		"images/69.png",
		"images/68.png",
		"images/92.png",
		"images/91.png",
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
			return alert("Parabéns você ganhou!!");
		}
	}
</script>

<svelte:head>
	<link rel="stylesheet" href="/styles/jogar2.css" />
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
