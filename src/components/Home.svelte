<script>
    import DarkMode from "./DarkMode.svelte";
    import Box from "./Box.svelte";

    import { onMount } from "svelte";
    import { isDark } from "./stores";
    import { writable } from 'svelte/store';
    
    let isLoaded = false;

    let hello = writable("");
    const hello_perm = "Hello!";
    let intro = writable("");
    const intro_perm = "Welcome to my page.";

    onMount(async() => {
        
        const body = document.querySelector('body');
        
        function toggleDarkMode() {
            let darkMode = $isDark;
            if (darkMode) {
            body.classList.add('dark-mode');
            } else {
            body.classList.remove('dark-mode');
            }
        }

        async function blinking(index, sentence, op) {
            if (index >= sentence.length) {
                return;
            }
            op.update(value => value + sentence[index]);
            await new Promise(resolve => setTimeout(resolve, 300));
            return blinking(index + 1, sentence, op);
        }

        await blinking(0, hello_perm, hello);
        await blinking(0, intro_perm, intro);
        
        // Call the function once on mount to set the initial mode
        toggleDarkMode();
        // Subscribe to changes in the store variable and update the mode accordingly
        isDark.subscribe(toggleDarkMode);

        setTimeout(()=>{
            isLoaded = true
        }, 1600)
    });

</script>
  

<div class="home-container">
    <span class="box">
        <h1> {$hello} </h1>
    </span>
   
    <DarkMode/>

    <div> 
        <span class="box">
            <h2> {$intro} </h2>
        </span>
    </div>
    {#if isLoaded}
    <div class="custom-links">
        <Box box_link="wwww.google.com" box_title="Github" />
        <Box box_link="wwww.google.com" box_title="Linkedin" />
    </div>
    {/if}    
</div>

<style>
    :global(:root){
        --main-color: green;
        --sec-color: rgb(10, 88, 27);
        --font-color: black;
    }
    :global(.dark-mode){
        --main-color: rgb(3, 1, 24);
        --sec-color: rgb(3, 23, 41);
        --font-color: white;
    }

    .home-container {
        display: flex;
        flex-direction: column;
        background-color:var(--main-color);
        height: var(--container-height);
        width: var(--container-width);
        align-items: flex-start;
        justify-content: center;
        font-family: 'Quantico', sans-serif;
        position: relative;
    }
    h1 {  
        font-size: 8rem;
        margin: 0.3rem 0;
        padding: 0.3rem 0;
    }
    h2 {
        margin: 0 0 0.3rem 0.6rem;
        padding: 0.3rem 0;
    }
    .box h1::after {
        content: "";
        width: 1rem;
        height: 7rem;
        background: var(--font-color);
        display: inline-block;
        animation: cursor-blink 0.5s 3;
        opacity: 0;
    }
    .box h1 {
        display: flex;
        align-items: center;
        gap: 2px;
    }
    .box h2 {
        display: flex;
        align-items: center;
        gap: 2px;
    }
    .box h2::after {
        content: "";
        width: 0.25rem;
        height: 1.5rem;
        background: var(--font-color);
        display: inline-block;
        animation: cursor-blink 0.5s 12 1.8s;
        opacity: 0;
    }
    @keyframes cursor-blink {
        0% {
            opacity: 0;
        }
        100%{
            opacity: 100;
        }
    }
   
    
    .custom-links{
        margin: 2rem;
        display:flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        position: absolute;
        bottom: 2rem;
        right: 3rem;
        animation: box-appear 1s;
    }

    @keyframes box-appear{
        0% {
            opacity:0;
        }
        50%{
            opacity: 50;
            transform: scale(1.05);
        }
        100%{
            opacity: 100;
            transform: scale(1.02);
        }
    }
    @media (max-width: 768px){
        .box h1{
            position: absolute;
            bottom: 27rem;
        }
        .box h2{
            position: absolute;
            bottom: 24rem;
        }
        .custom-links{
            position : absolute;
            bottom: 8rem;
            left: 6rem;
    }
    }
</style>