<script>
    import Home from "../components/Home.svelte";
    import About from "../components/About.svelte";
    import Skills from "../components/Skills.svelte";
    import Projects from "../components/Projects.svelte";
    import ContactMe from "../components/ContactMe.svelte";
</script>

<div class="main-container">
    <Home/>
    <About/>
    <Skills/>
    <Projects/>
    <ContactMe/>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Quantico:wght@700&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700;900&display=swap');
    :global(body,html) {
        margin: 0;
        padding: 0;
        height: 100vh;
        width: 100%;
    }
    :global(:root){
        --container-width: 100%;
        --container-height: 100vh;
    }
    .main-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        color: var(--font-color);
    }
</style>
