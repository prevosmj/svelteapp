<style>
    button{
        font: inherit;
        padding: 0.15rem 0.5rem;
        background: rgb(71, 0, 121);
        border: 1px solid rgb(71, 0, 121);
        color: whitesmoke;
        cursor: pointer;
    }
    button:hover,
    button:active{
        box-shadow: 1px 1px 6px rgba(0,0,0,0.25);
    }
</style>

<button on:click>
    <slot />
</button>