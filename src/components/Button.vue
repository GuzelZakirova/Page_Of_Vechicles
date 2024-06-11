<script setup lang="ts">

</script>

<template>
    <button class="primary_red text_white">
        <img src="../assets/icons/plus.svg" alt="add">
        <slot></slot>
    </button>
</template>

<style scoped>
button {
    padding: 9px 18px;
    display: flex;
    gap: 16px;
    align-items: center;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}
</style>