<script>
    export let input;

    let api = `https://api.github.com/users/${input}`;

    let avatar_url;
    let name = '';
    let blog = '';
    let location = '';
    let bio = '';

 
    fetch(api)
    .then(response => {
        return response.json();
    })
    .then(data => {
        avatar_url = data.avatar_url;
        name = data.name;
        blog = data.blog;
        location = data.location;
        bio = data.bio;
    })
    .catch(err => {
        console.log("Error while formatting weather info: ", err)
    })
    .catch(err => {
        console.log("Error while fetching API data: ", err)
    }); 

</script>

<div class="personal">
    <div class="rnd-img">
        <img src="{ avatar_url }" alt="">
    </div>
    <div>
        <h1>{ name }</h1>
        <h3>{ location }</h3>
        <a href="{ blog }">{ blog }</a>
        <p>{ bio }</p>
    </div>
</div>

<style>
    .personal{
        max-width:100vw;
        display:flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        text-align: right;
        margin:.75rem;
    }
    .rnd-img{
        width:200px;
        height:200px;
        border-radius: 50%;
        overflow:hidden;
    }
    img{
        width:100%;
        height:100%;
    }
    @media screen and (min-width:1024px){
        .personal{
            flex-direction: row;
        }
    }
</style>
