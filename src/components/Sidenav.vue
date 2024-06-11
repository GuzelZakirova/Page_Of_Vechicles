<script setup lang="ts">

</script>

<template>
    <div class="sidenav text_white primary_dark">
        <div class="title">Demo Test</div>
        <div class="nav text_white45">
            <div class="nav__option nav_font">
                <img src="../assets/icons/user.svg" alt="user">
                <span>Profile</span>
            </div>
            <div class="nav__option nav_font text_white secondary_white20" id="selected">
                <img src="../assets/icons/rim.svg" alt="vech">
                <span>Vechicles</span>
            </div>
            <div class="nav__option nav_font">
                <img src="../assets/icons/settings.svg" alt="settings">
                <span>Setting</span>
            </div>
        </div>
        
    </div>
</template>

<style scoped>
.sidenav {
    display: block;
    float: left;
    width: 256px;
    height: 100%;
    background-image: url(../assets/icons/design.svg);
    background-repeat: no-repeat;
    background-position: bottom;
}
.title {
    font-family: 'DMSans-Bold';
    font-size: 24px;
    line-height: 24px;
    margin-top: 30px;
    text-align: center;
}
.nav {
    display: flex;
    flex-direction: column;
    gap: 16px;
    margin-top: 102.55px;
}
.nav__option {
    display: flex;
    gap: 20px;
    align-items: center;
    padding: 12px 30px;
    cursor: pointer;
}
#selected {
    border-left: 2px solid #D90E32;
}
</style>