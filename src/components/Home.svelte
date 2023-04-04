<script>
    import DarkMode from "./DarkMode.svelte";
    import { onMount } from "svelte";
    import { isDark } from "./stores";

    let hello = "";
    const hello_perm = "Hello!";
    let intro = "";

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

        
    function blinking(index) {
      let visible = true;
      if (index >= hello_perm.length) {
        return;
      }
        hello += hello_perm[index];
    //   setInterval(() => {
	// 		visible = !visible;
	// 		cursor.style.opacity = visible ? "1" : "0";
	// 	}, 50);
      
      setTimeout(() => {
        blinking(index + 1);
      }, 1000);
    }
    
    blinking(0);
  
  // Call the function once on mount to set the initial mode

    toggleDarkMode();

  
  // Subscribe to changes in the store variable and update the mode accordingly
  isDark.subscribe(toggleDarkMode);
        });
</script>
  

<div class="home-container">
    <span class="box">
        <h1> {hello} </h1>
    </span>
   
    <DarkMode/>
    <h2> {intro}</h2>
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
        animation: cursor-blink 0.5s 15;
        opacity: 0;
    }
    .box h1 {
        display: flex;
        align-items: center;
        gap: 2px;
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