<script>
    import DarkMode from "./DarkMode.svelte";
    import { onMount } from "svelte";
    import { isDark } from "./stores";
    import { writable } from 'svelte/store';
    
    let hello = writable("");
    const hello_perm = "Hello!";
    let intro = writable("");
    const intro_perm = "Welcome to my page...";

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
</div>

<style>
    :global(:root){
        --main-color: rgb(10, 88, 27);
        --sec-color: green;
        --font-color: black;
    }
    :global(.dark-mode){
        --main-color: purple;
        --sec-color: violet;
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
        animation: cursor-blink 0.5s 5;
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
        animation: cursor-blink 0.5s 10 4s;
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
</style>
