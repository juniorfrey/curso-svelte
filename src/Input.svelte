<script>
    import Movie from './Peliculas.svelte';
    let value = '';
    //let loading = false;
    let respuesta = [];
    const handleInput = (event) => value = event.target.value;
    $: if(value.length > 2){
        respuesta =  fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
            //.then(req => !req.ok() && new Error('dadada'))
            .then(res => res.json())
            .then(apiResponse => apiResponse.Search || [] )
    }
    
</script>

<main>
    <input type="text" value={value} on:input={handleInput} placeholder="Busca tu pelicula">

    {#await respuesta}
        <strong>Cargando .........</strong>
    {:then peliculas}
        {#each peliculas as {Poster, Title, Year}, index}
            <Movie
                title={Title}
                poster={Poster}
                year={Year}
            />
        {:else}
            <strong>No hay peliculas</strong>
        {/each}
    {:catch error}
            <p>{error} Error</p>
    {/await}
  

</main>