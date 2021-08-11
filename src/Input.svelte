<script>
    let value = '';
    let loading = false;
    let respuesta = [];
    const handleInput = (event) => value = event.target.value;
    $: if(value.length > 2){
        loading = true;
        fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
            .then(res => res.json())
            .then(apiResponse => {
                console.log(apiResponse);
                respuesta = apiResponse.Search || [];
                loading = false;
            })
    }
    
</script>

<main>
    <input type="text" value={value} on:input={handleInput} placeholder="Busca tu pelicula">

    {#if loading}
        <strong>Cargando .........</strong>
    {:else}
        {#if respuesta.length > 0}
            <strong> Tenemos {respuesta.length} peliculas </strong>
        {:else}
            <strong> No hay peliculas </strong>
        {/if}
    {/if}

   

</main>