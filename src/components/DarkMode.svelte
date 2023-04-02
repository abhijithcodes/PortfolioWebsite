<script>
    import { isDark } from "./stores";

    let isButtonActive = {"sun": false, "moon": false}

    function handleFocus(id){
        isButtonActive = {...isButtonActive, [id]: true}
        setTimeout(()=>{
            isButtonActive = {"sun": false, "moon": false}
        }, 1000)
    }

    function handleClick(id){
        if(id==="moon"){
            isDark.set(true)
        }else{
            isDark.set(false)
        }
    }

</script>

<div class="buttons-container">
    <button class="sun">
        <i class="fa-solid fa-sun"
         on:mouseover={()=>handleFocus("sun")} 
         on:focus={()=>handleFocus("sun")} 
         on:click={()=>handleClick("sun")}
         class:spin={isButtonActive.sun}></i>
    </button>
    <button >
        <i class="fa-regular fa-moon"
        on:mouseover={()=>handleFocus("moon")} 
        on:focus={()=>handleFocus("moon")} 
        on:click={()=>handleClick("moon")}
        class:spin={isButtonActive.moon} ></i>
    </button>
</div>
<style>
    button{
        text-align: center;
        padding: 0.6rem;
        margin: 0.4rem;
        width: 3.5rem;
        background-color: var(--main-color);
        border: none;
        box-shadow: none;
        border-radius: 5rem;
    }

    .fa-sun{
        font-size: 2rem;
    }
    .fa-moon{
        font-size: 2rem;
    }
    .buttons-container {
        position: absolute;
        top:2rem;
        right:0.2rem;
        padding: 0.9rem;
    }
    .spin{
        animation: spin 1s linear;
    }
    @keyframes spin {
        0% {
      transform: scale(1)rotate(0deg);
    }
    50%{
        transform: scale(1.5)rotate(180deg);
    }
    100% {
      transform: scale(1)rotate(360deg);
    }
    }
</style>