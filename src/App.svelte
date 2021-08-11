
<script>
	import Contador from './Contador.svelte';
	import Input from './Input.svelte';

	/* Props */
	const commonProps = {maxCounter : 5};

</script>

<Contador inicialConteo={2} {...commonProps}/>
<Input/>