<script>
    export let navigate
    export let timers =  {
        name: 'TestTmer',
        duration: 1800000,
        timers: [
        
            {
                name: 'Warm Up',
                color: '#a6a1a1',
                duration: 5 * 60000
            },
            {
                name: 'Hign Intensity',
                color: '#1dcf1d',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#ed1b0c',
                duration: 4 * 60000 
            },
            {
                name: 'Hign Intensity',
                color: '#1dcf1d',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#ed1b0c',
                duration: 4 * 60000 
            },
            {
                name: 'Hign Intensity',
                color: '#1dcf1d',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#ed1b0c',
                duration: 4 * 60000 
            },
            {
                name: 'Cool Down',
                color: '#9de7f2',
                duration: 2 * 60000 
            }
            
        ]
    }

    let currentInterval = 0
    let elapsed = 0
    let remaining = 0

    const prettyTime = ms => {
        const seconds = (ms / 1000) % 60
        const minutes = (ms / 60000) % 60
        const hours = (ms / 3600000) % 24

        const mStr = `${minutes < 10 ? '0' : ''}${minutes}`
        const sStr = `${seconds < 10 ? '0' : ''}${seconds}`

        if (hours < 1) {
            return `${mStr}:${sStr}`
        }
        
        return `${hours}:${mStr}:${sStr}`
    }

      //  🔒

</script>

<style>
    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        padding: 0;
        margin: 0;
        background-color: var(--color);
    }
    .countdown {
        flex: 1;
        width: 100%;
        padding: 0;
        margin: 0;
        font-size: 11em;
        text-align: center;

    }
    .time-remaining {
        flex: 1;
        width: 100%;
        display: flex;
        justify-content: space-evenly;
        padding: 0;
        margin: 0;


    }
    .timers-container {
        flex: 3;
        width: 100%;
      
        padding: 0;
        margin: 0;
        overflow-y: scroll; 
    }
    .timer {
        height: 50%;
        flex: 1;
        border-radius: 8px;
        margin: 0;
    }
    nav {
        flex: .5 ;
        width: 100%;
        align-self: flex-end;
        padding: 0;
        margin: 0;

    }
    .time-interval--info>figcaption {
       text-transform: uppercase;
       font-size: x-small;
       margin:0;
    }
    .time-interval--info>span {
        font-weight: 700;
        font-size: 1.3em;
    }
  
</style>


<main style="--color: {timers.timers[currentInterval].color}">
   <div class="countdown">
      5:00
   </div>
   <div class="time-remaining">
       <figure class="time-interval--info">
        <figcaption>elapsed</figcaption>
       <span>{prettyTime(elapsed)}</span>
       </figure>
       
       <figure class="time-interval--info">
        <figcaption>interval</figcaption>
        <span>{`${currentInterval}/${timers.timers?.length}`}</span>
       </figure>
       <figure class="time-interval--info">
           <figcaption>remaining</figcaption>
           <span>{prettyTime(timers.duration - remaining)}</span>
       </figure>
      
   </div>
   <div class="timers-container">
      {#each timers.timers as timer, idx }
        <div class="timer" style="background-color: {timer.color}">
            {#if idx === currentInterval}
                <div>current interval</div>
            {:else if idx === currentInterval + 1}
                <div>up next</div>
            {/if}
            <div>{timer.name}</div>
            <div>{prettyTime(timer.duration)}</div>
        </div>
      {/each}
   </div>
   <nav>
    ✖ 🔓  ⟳ ► 
   </nav>
</main>