<div class="about-container">
    <h2> About Me</h2>
    <section class="about-me">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </section>
</div>

<style>
    .about-container{
        height: var(--container-height);
        width: var(--container-width);
        display: flex;
        flex-direction: column;
        background-color: var(--sec-color);
        font-family: 'Lato', sans-serif;
    }
     h2 {  
        font-size: 4rem;
        margin: 1rem 0.5rem;
        padding: 0.3rem 0.1rem;
        height: 30vh;
        align-self: flex-end;
    }
    .about-me{
        width: 60vw;
        padding: 0.3rem;
        margin: 0.5rem 1rem;
        align-self: center;
    }
    p{
        font-size: 1.1rem;
        column-count: 2;
        column-gap: 2rem;
    }
</style>