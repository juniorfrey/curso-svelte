<script>
    export let  poster, title, year;
</script>
<style>
    img{
        border-radius: 50%;
    }
</style>


 <article>
   <img src={poster} alt={title} width="100px" height="100px">
    <h3> {title} - {year}  </h3>
</article>