<script>
    export let message='Something exciting just happened!';
    export let isCongrats = false;

    export let showModal = false;
</script>

{#if showModal}
<div class="backdrop" class:congrats={isCongrats} on:click>
    <div class="modal">
        <p>{message}</p>
    </div>
</div>
{/if}

<style>
.backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0,0,0,0.8)
}
.modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
}
.congrats .modal {
    background: crimson;
    color: white;
}
</style>