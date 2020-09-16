<script>
    import Timer from './Timer.svelte';
    import HowTo from './HowTo.svelte';
    let audio;
    function runAudio({detail}) {
        if (detail === 'play') {
            audio.play()
        }
    }
</script>
<style>
    h1, h3 {
        text-align: center;
    }

</style>
<h1>Handwashing app</h1>
<Timer on:wash_complete={runAudio}/>
<HowTo />

<h3>
    <a href="https://www.who.int/gpsc/clean_hands_protection/en/" target='_blank'>Picture source</a>
    <a href="https://freesound.org/people/metrostock99/sounds/345086/" target='_blank'>Sound source</a>
</h3>

<audio bind:this={audio}> 
    <track kind='captions'/>
    <source src='ohyee.mp3' />
</audio>