<script setup lang="ts">
defineProps({
    name: String,
    vin: String,
    url: String,
    uploads: Number
})
</script>


<template>
    <div class="card primary_light-grey">
        <img class="icon" src="../assets/icons/more_horizontal.svg" alt="more">
        <img class="photo" :src="url" alt="car">
        <div class="description">
            <div class="name text_black">{{ name }}</div>
            <div class="vim text_grey">{{ vin }}</div>
            <div class="border"></div>
            <div class="description__down">
                <div class="uploads" :class="uploads == 30 ? 'secondary_green text_green' : 'secondary_grey text_dark-grey'">
                    <img v-if="uploads == 30" class="check-icon" src="../assets/icons/check.svg" alt="check">
                    {{ uploads }}/30
                </div>
                <span class="text text_grey">3 days left</span>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    width: 354px;
    border-radius: 10px;
    position: relative;
}
.icon {
    position: absolute;
    top: 20px;
    right: 20px;
}
.photo {
    width: 260px;
    margin: 40px 47px 24px 47px;
}
.description {
    margin: 0 39px 16px 24px;
}
.name {
    font-family: 'DMSans-Bold';
    font-size: 20px;
    line-height: 22px;
    margin-bottom: 12px;
}
.vim {
    font-family: 'DMSans-Medium';
    font-size: 15px;
    line-height: 20px;
}
.uploads {
    padding: 4px 14px;
    border-radius: 6px;
    display: flex;
    align-items: center;
}
.text {
    font-family: "DMSans-Medium";
    font-size: 15px;
    line-height: 16px;
}
.border {
    border-top: 1px solid #E4E4E4;
    margin: 18px 0;
}
.description__down {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.check-icon {
    margin-right: 8px;
    width: 16px;
    height: 16px;
}
</style>