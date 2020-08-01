<script>
    import { onMount } from 'svelte';
    import Clipboard from './Clipboard.svelte';
   
    export let name = '';
    export let repoCount;
    export let popularName = '';
    export let popularUrl = '';
    export let popularDesc = '';
    export let popularClone = '';
    export let popularFork = '';
</script>



<div id="stats-wrap">
    <h2 id="repo-count">{ name } has { repoCount } repositories</h2>
    <h3>most popular repository is : <a href="{ popularUrl }" target="blank">{ popularName }</a></h3>
    <h4>{ popularDesc }</h4>
    <h5>{ popularName } has been forked { popularFork } times</h5>
    <div id="clip-cont">
        <label for="clone">clone it!</label>
        <input type="text" name="clone" value="{ popularClone }">
        <Clipboard value={ popularClone } />
    </div>
</div>

<style>
    #stats-wrap{
        display:flex;
        flex-direction: column;
        align-items: center;
        margin:0 2rem;
    }
    #clip-cont{
        margin:2rem;
        padding:1.25rem;
        border:1.5px dashed #909CC2;
        border-radius:5px;
    }
    #repo-count{
        margin:2rem;
    }
</style>