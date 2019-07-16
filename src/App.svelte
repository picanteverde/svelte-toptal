<script>
import Search from './Search.svelte'
import Post from './Post.svelte'
const getPosts = async (search) => {
  const res = await fetch(`https://codingthat-quick-json-back-end-2.glitch.me/posts?q=${search}`)
  return await res.json()
}

let res, loading;
const search = async (value) => {
  loading = true;
  res = await getPosts(value)
  loading = false;
}
</script>
<style>
div{
  width: 70%;
  min-width: 300px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 30px;
}
@media (max-width: 450px) {
  div{
    width: 100%;
    margin-top: 4px;
  }
}
</style>
<Search {search} {loading}/>
{#if res}
  {#await res then posts}
    {#if posts.length}
      <div>
      {#each posts as post}
        <Post {...post}/>
      {/each}
      </div>
    {:else}
      <div>no results</div>
    {/if}
  {/await}
{/if}