<script>
    import DarkMode from "./DarkMode.svelte";
    import { onMount } from "svelte";
    import { isDark } from "./stores";

    onMount(() => {
        const body = document.querySelector('body');
        
        function toggleDarkMode() {
            let darkMode = $isDark;
            if (darkMode) {
            body.classList.add('dark-mode');
            } else {
            body.classList.remove('dark-mode');
            }
        }
  
  // Call the function once on mount to set the initial mode
  toggleDarkMode();
  
  // Subscribe to changes in the store variable and update the mode accordingly
  isDark.subscribe(toggleDarkMode);
        });

</script>

<div class="home-container">
    <h1> Hello! </h1>
    <DarkMode/>
    <h2> This is Abhijith Mammoottil</h2>
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
        align-items: left;
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
</style>
       