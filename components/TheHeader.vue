<template>
    <div>
        <div class="header">
            <div class="logo">
                <NuxtLink to="/">
                    <img src="@/assets/logo.png">
                </NuxtLink>
            </div>
            <div @click="show=!show" class="icon">
                <font-awesome-icon
                    v-if="!show"
                    icon="fa-solid fa-bars" 
                    class="icon-menu" 
                />
                <font-awesome-icon 
                    v-if="show"
                    icon="fa-solid fa-xmark" 
                    class="icon-menu" 
                />
            </div>
        </div>
        <div v-if="show" class="menu">
            <div v-for="(item,i) in pages" :key="i" class="menu-item">
                <NuxtLink @click="show=!show" :to="item.to">
                    {{ item.label }}
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data: () => ({
        show: false,
        pages: [
            {
                label: 'О нас',
                to: '/about'
            },
            {
                label: 'Контакты',
                to: '/contacts'
            }
        ]
    })
})
</script>

<style scoped>
.header {
    display: flex;
    justify-content: space-between;
    height: 60px;
    background-color: black;
    color: whitesmoke;
}
.icon-menu {
    font-size: 30px;
    cursor: pointer;
}
.icon {
    display: flex;
    align-items: center;

    margin-right: 5%;
}
.logo {
    display: flex;
    align-items: center;

    margin-left: 5%;
}
.logo img {
    max-height: 30px;
}

.menu {
    background-color: black;
    color: whitesmoke;
    padding: 10px 0;
}
.menu-item {
    padding: 7.5px 5%;
}
a {
    text-decoration: none;
    color: whitesmoke;
}
</style>