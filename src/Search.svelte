<script>
	export let search
	export let loading

	let value = ''
	$: disabled = loading;
	const handleSearch = () => search(value)

	const keyDown = (e) => (e.keyCode === 13) && search(value)

</script>
<style>
	.search {
		height: 60px;
	}
	.search>img{
		height: 60px;
	}
	.search>div{
		height: 60px;
		display: inline-block;
		vertical-align: top;
    text-align: center;
		width: calc(100% - 229px);
		padding-top: 4px;
	}
	.search>div>input{
		width: 200px;
		height:  36px;
	}
	.search>div>button{
		height: 36px;
		width: 36px;
    vertical-align: bottom;
	}
	@media (max-width: 450px) {
		.search {
			height: 40px;
		}
		.search>div>input{
			width: 133px;
			height:  36px;
		}
		.search>img {
			height: 36px;
		}
		.search>div {
			height: 40px;
			width: calc(100% - 142px);
		}
	}
</style>
<div class="search">
	<img src="https://svelte.dev/svelte-logo-horizontal.svg" alt="svelte logo"/>
	<div class="search-box">
		<input type="text" bind:value={value} on:keydown={keyDown} {disabled} />
		<button on:click={handleSearch} {disabled} >🔎</button>
	</div>
</div>
