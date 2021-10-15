
<script>
    let show = false;
    export const toogle = () => {
        show =! show; 
        // console.log(show)
    }

    const handleKeydown = (e) => {
        // console.log(e.keyCode)
        if (e.keyCode == 27) {
            show=false;
        }
    }

</script>

<svelte:window on:keydown={handleKeydown}/>

{#if show}
<div class="modal-container">
    <div class="modal-content">
        <span on:click={toogle} class="close-cross"><i class="fas fa-times-circle"></i></span>
        <slot />
    </div>
</div>
{/if}

<style lang='scss'>
    @import '../../vars.scss';

    .modal-container {
        background-color: rgb(0,0,0);
        background-color: rgba(0,0,0, .5);
        
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
    }

    .modal-content {
        background-color: $white;
        max-width: 50%;
        height: 300px;
        padding: $pL;
        margin: 15% auto;
        display: flex;
        justify-content: space-around;
        align-items: center;
        
    }

    .close-cross {
        position: absolute;
        top: 10px;
        right: 20px;
        float: right;
        cursor: pointer;
    }

</style>