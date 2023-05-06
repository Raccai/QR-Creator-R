<script>
    export let active = true;
</script>

<div class:isActive = {active == true}>
    <slot></slot>
</div>

<style>
    div {
        background-color: white;
        width: 300px;
        height: 70px;
        padding: 30px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 20px;
        transition: all 0.1s ease;
    }

    .isActive {
        background-color: white;
        width: 300px;
        height: 370px;
        padding: 30px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 20px;
        transition: all 0.1s ease;
    }
</style>