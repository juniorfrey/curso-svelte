<script>
    let value = '';
    let respuesta = [];
    const handleInput = (event) => value = event.target.value;
    $: if(value.length > 2){
        fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
            .then(res => res.json())
            .then(apiResponse => {
                console.log(apiResponse);
                respuesta = apiResponse.Search;
            })
    }
    
</script>

<main>
    <input type="text" value={value} on:input={handleInput}>
</main>