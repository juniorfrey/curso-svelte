<script>
	let name = 'desarrollo';
	export let inicialConteo = 0;
    export let maxCounter = 9;
	let contador = inicialConteo;

	/* Funcion para cambiar texto a la variable name*/
	function handleClick(){
		name = 'Development';
	}

	function IncrementarContador(){
		contador++;
	}

    // Indicamos uan declaración reactiva -> "$:""
    $: esPar_Impar = contador % 2 === 0 ? `Es par` : `Es Impar`;
    $: {
        if(contador > maxCounter)
            contador = maxCounter;
    }

</script>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<main>
	<h1>Ambiente de  {name}!</h1>
	<button on:click={handleClick}>Cambiar nombre</button>
	<button on:click={IncrementarContador}>Incrementar contador</button>
	<span>{contador}</span>
    <span> {esPar_Impar} </span>
</main>