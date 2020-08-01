<script>
    export let avatar_url;
    export let name = '';
    export let blog = '';
    export let location = '';
    export let bio = '';
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
        text-align: center;
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
            text-align: right;
            flex-direction: row;
        }
    }
</style>
