<script>
	// import Header from './Header.svelte';
    import Personal from './Personal.svelte';
    import Stats from './Stats.svelte';

    let input = 'stordahl';
    let repoCount;
    let stargazerCount = 0;
    let popularData = '';

    //Props Objects
    let personal = {
        avatar_url: '',
        name: '',
        blog: '',
        location: '',
        bio: ''
    };
    let stats = {
        repoCount:'',
        name : '',
        popularName : '',
        popularUrl : '',
        popularDesc : '',
        popularClone : '',
        popularFork : ''
    };

    function apiFetch(){
        //First Call for Personal Data
        fetch('https://api.github.com/users/' + input)
        .then(response => {
            return response.json();
        })
        .then(data => {
            personal.avatar_url = data.avatar_url;
            personal.name = data.name;
            personal.blog = data.blog;
            personal.location = data.location;
            personal.bio = data.bio;
        })
        .catch(err => {
            console.log("Error while formatting weather info: ", err)
        })
        .catch(err => {
            console.log("Error while fetching API data: ", err)
        }); 

        //Second Call for Statistics
        fetch('https://api.github.com/users/' + input + '/repos')
        .then(response => {
            return response.json();
        })
        .then(data => {
            //Number of Repos
            repoCount = data.length;
            //Calculate Most Popular Repo Based on Stars
            data.forEach(repo => {
                if(repo.stargazers_count >= stargazerCount){
                    popularData = repo;
                }
            });
            //Assign Data from Most Popular Repo
            stats.name = popularData.owner.login;
            stats.popularName = popularData.name;
            stats.popularUrl = popularData.html_url;
            stats.popularDesc = popularData.description;
            stats.popularClone = popularData.clone_url;
            stats.popularFork = popularData.forks_count;
    
        })
        .catch(err => {
            console.log("Error while formatting weather info: ", err)
        })
        .catch(err => {
            console.log("Error while fetching API data: ", err)
        })
    }
    apiFetch();
</script>


<header>
    <h2>github<strong>Dash</strong></h2>
    <div>
        <button on:click={ apiFetch }>search</button>
        <input type="text" bind:value={ input } >
    </div>
</header>
<div id="dashboard">
    <Personal {...personal}/>
    <Stats {...stats}/>
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