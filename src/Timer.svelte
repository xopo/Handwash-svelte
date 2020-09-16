<script>
    import { onDestroy } from 'svelte';
    import ProgressBar from "./ProgressBar.svelte";
    
    const totalSeconds = 20;
    
    let progress = 0;
    let secondLeft = totalSeconds;
    
    let disableButton = false;

    const startTimer = () => {
        disableButton = true;
        const  timer = setInterval(() => {
            secondLeft = secondLeft - 1;
            progress = ((totalSeconds - secondLeft) / totalSeconds) * 100; // 100 - secondLeft * 5;
            if ( secondLeft < 1 ) {
                clearInterval(timer);
                secondLeft = totalSeconds;
                disableButton = false;
            }
        }, 1000);
    }
    onDestroy(() => {
        clearInterval(timer);
    })
</script>
<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: rgb(154, 73, 73);
        width: 100%;
        margin: 10px 0;
        border-radius: 5px;
    }
    .start:hover {
        background-color: rgb(105, 57, 57);
        box-shadow: 0 0 0 1pt red;
    }
    .start:active {
        background: red;
        outline-color: black;
    }
    .start:disabled {
        background-color: #aaa;
        cursor: not-allowed;
        box-shadow: none;
    }
    .start:disabled:hover {
        box-shadow: 0 0 0 1pt black;
    }
</style>
<div bp='grid'>
    <h2 bp='offset-5@md 4@md 12@sm'>Seconds left: {secondLeft}</h2>
</div>
<ProgressBar {progress}/>
<div bp='grid'>
    <button 
        disabled={disableButton}
        bp='offset-5@md 4@md 12@sm' 
        on:click={startTimer}
        class='start'>Start</button>
</div>