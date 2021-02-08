<script>
    export let navigate
    export let timers =  {
        name: 'TestTmer',
        duration: 1800000,
        timers: [
        
            {
                name: 'Warm Up',
                color: '#123aab',
                duration: 5 * 60000
            },
            {
                name: 'Hign Intensity',
                color: '#123aab',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#123aab',
                duration: 4 * 60000 
            },
            {
                name: 'Hign Intensity',
                color: '#123aab',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#123aab',
                duration: 4 * 60000 
            },
            {
                name: 'Hign Intensity',
                color: '#123aab',
                duration: 3 * 60000
            },
            {
                name: 'Low Intensity',
                color: '#123aab',
                duration: 4 * 60000 
            },
            {
                name: 'Cool Down',
                color: '#123aab',
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
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 0;
        margin: 0;

        
    }
    nav {
        flex: .5 ;
        width: 100%;
        align-self: flex-end;
        padding: 0;
        margin: 0;

    }
</style>


<main style="--color: {timers.timers[currentInterval].color}">
   <div class="countdown">
      5:00
   </div>
   <div class="time-remaining">
       <div>
        <div>elapsed</div>
        <div>{prettyTime(elapsed)}</div>
       </div>
       
       <div>
        <div>interval</div>
        <div>{`${currentInterval}/${timers.timers?.length}`}</div>
       </div>
       <div>
           <div>remaining</div>
           <div>{prettyTime(timers.duration - remaining)}</div>
       </div>
      
   </div>
   <div class="timers-container">
       <div class="timer">
           currnt interval
           Warn Up
           5:00
       </div>
       <div class="timer">
        up next
        High Intensity
       4:00
    </div>
   </div>
   <nav>
       close lock restart play
   </nav>
</main>