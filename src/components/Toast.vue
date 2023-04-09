<template>
    <div class="body">
        <div id="toast">
            <div class="toast">
                <div class="toast__icon">
                    <font-awesome-icon :icon="['fas', 'circle-check']" />
                </div>
                <div class="toast__body">
                    <h3 class="toast__title">Đã lưu thành công</h3>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
#toast {
    position: fixed;
    top: 32px;
    right: 32px;
}
.body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
.toast {
    display: flex;
    align-items: center;
    background-color: #fff;
    border-radius: 2px;
    padding: 5px 0;
    border-left: 4px solid #47d864;
    box-shadow: 0 5px 8px rgba(0, 0, 0, 0.3);
    min-width: 200px;
    animation: sliderInLeft ease .3s, fadeOut linear 1s 3s forwards ;
}

@keyframes sliderInLeft {
    from {
        opacity: 0;
        transform: translateX(calc(100% + 32px));
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

@keyframes fadeOut {
    to {
        opacity: 0;
    }
}

.toast__body {
    padding-left: 10px;
    color: #47d864;
    flex-grow: 1;
}
</style>