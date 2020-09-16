<script>
    export let progress = 5;
</script>
<style>
    .progress-container {
        margin: 20px 0;
        outline: 1px solid #aaa;
    }
    .progress-bar {
        height: 30px;
        background: rgb(77, 199, 55);
    }
</style>
<div bp='grid'>
    <div 
        bp='offset-5@md 4@md 12@sm'
        class='progress-container'>
        <div class="progress-bar" style={`width: ${progress}%`}>
            <span class='sr-only'>{progress}%</span>
        </div>

    </div>
</div>