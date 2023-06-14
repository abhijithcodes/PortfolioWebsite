<script>
    export let box_link;
    export let box_title;
</script>

<div class="link-box">
    <a class="link" href={box_link}>{box_title}</a>
</div>

<style>
    .link-box{
        height: 2rem;
        width: 6rem;
        border: 2px solid #000; /* Outline border with 2px width and black color */
        text-align: center; /* Center align the text within the box */
        display: flex; /* Use flexbox for vertical and horizontal centering */
        justify-content: center; /*Center align horizontally*/
        align-items: center; /*Center align vertically*/
        padding: 1.5rem;
        margin: 1rem;
    }

    .link {
    text-decoration: none; /* Remove underline */
    color: currentColor; /* Use current color from parent element */
    font-size: 2rem;
    }

    .link-box:hover{
        animation: scaling 0.5s;
        background-color: rgb(9, 212, 36);
    }

    @keyframes scaling {
        0%{
            transform: scale(1);
        }
        50%{
            transform: scale(1.03);
        }
        100%{
            transform: scale(1);
        }
    }
    @media(max-width:768px){
        .link-box{
            height: 2rem;
            width: 4rem;
            border: 2px solid #000; /* Outline border with 2px width and black color */
            text-align: center; /* Center align the text within the box */
            display: flex; /* Use flexbox for vertical and horizontal centering */
            justify-content: center; /*Center align horizontally*/
            align-items: center; /*Center align vertically*/
            margin: 0.5rem;
    }
    .link {
        text-decoration: none; /* Remove underline */
        color: currentColor; /* Use current color from parent element */
        font-size: 1.5rem;
    }
    }
</style>