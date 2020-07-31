<script>
	// import Header from './Header.svelte';
    import Personal from './Personal.svelte';
    import Stats from './Stats.svelte';

    let input = 'stordahl';

//    let api = `https://api.github.com/users/${input}`;
    // let repoApi = api + '/repos';

</script>

<!-- <Header /> -->
<header>
    <h2>github<strong>Dash</strong></h2>


        <!-- <button >search</button> -->
        <input type="text" bind:value={ input }>
    
</header>
<div id="dashboard">
    <Personal input={input}/>
    <Stats input={input}/>
</div>

<style>
    header{
        width:100vw;
        height:60px;
        background-color: #084887;
        color:#F7F5FB;
        display: flex;
        align-items: center;
        justify-content: space-between;
        box-shadow: 0px 3px 10px #505050;
        padding: 0 2rem;
    }
    h2{
        margin:1rem;
    }
    input, button{
        margin:0;
    }
    #dashboard{
        width:100vw;
        margin:3rem 0;
    }

</style>