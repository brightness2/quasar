<template>
    <div>
        <div class="row items-center justify-center q-pt-sm">
            <div class="box">
               <q-icon name="bi-camera" size="lg" color="grey-6"></q-icon>
            </div>
        </div>
        <div class="row items-center justify-center q-pa-md">
            <div class="box q-mr-md q-mt-md" v-for="(image,index) in images" :key="index">
                <q-avatar>
                    <img :src="image.url" :title="image.title">
                </q-avatar>
            </div>
        </div>
    </div>
</template>

<script setup>
const images = [
    {title:'avatar',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
    {title:'dev',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
    {title:'avatar',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
    {title:'dev',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
    {title:'avatar',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
    {title:'dev',url:'https://cdn.quasar.dev/img/boy-avatar.png'},
];
</script>

<style lang="scss" scoped>
.box{
    display:flex ;
    justify-content: center;
    align-items: center;
    width: 20vw;
    height: 20vw;
    border: 1px solid #ccc;
}
</style>