<script>
    export let navigate;
</script>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    ul {
        display: flex;
        flex-direction: column;
        list-style-type: none;
        margin: 0 5px;
        padding: 0;

       

    }
    li {
        flex: 1;
        border: 1px solid pink;
        text-align: center;
        padding: 5px;
        margin: 2px 0;
    }

</style>


<main>
   <h2>Select a timer or create a new one</h2>
   <ul class="timer-container">
       <li>
           <button on:click={() => navigate('timer')}>Basic HIIT</button>
       </li>
       <li>Advanced HIIT</li>
       <li>THe third example</li>
   </ul>
</main>