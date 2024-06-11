<script setup lang="ts">
defineProps({
    total: Number
})
</script>

<template>
    <div class="header">
        <div class="title">
            <h1 class="text_black">Vechicles</h1>
            <div class="number primary_light-grey text_dark-grey">{{ total }}</div>
        </div>
        <div class="settings">
            <img class="button" src="../assets/icons/add.svg" alt="lang">
            <div class="profile">
                <img src="../assets/icons/photo.png" alt="lang">
                <span class="text3_font">John Doe</span>
            </div>
            <div class="lang">
                <img src="../assets/icons/uk.svg" alt="lang">
                <div class="lang_title text3_font">En</div>
                <div class="arrow"><img src="../assets/icons/arrow_down.svg" alt="lang"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.header {
    margin-top: 30px;
    height: 72px;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #E4E4E4;
    padding: 0 30px;
}
.title {
    display: flex;
    gap: 18px;
    align-items: center;
}
.number {
    padding: 4px 14px;
    border-radius: 6px;
    font-family: 'DMSans-Bold';
    font-size: 15px;
    line-height: 22px;
}
.settings {
    display: flex;
    align-items: center;
}
.button {
    margin-right: 40px;
    cursor: pointer;
}
.profile {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-right: 32px;
}
.lang {
    display: flex;
    align-items: center;
}
.lang_title {
    margin-right: 3px;
    margin-left: 14px;
}
.arrow {
    width: 24px;
    height: 24px;
    text-align: center;
    cursor: pointer;
}
</style>
