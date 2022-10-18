<template>
    <div>
        <div class="row justify-center q-pt-sm">
            <p class="text-h5">信息</p>
        </div>
        <div class="q-pa-md" style="max-width: 350px">
            <q-list dense bordered padding class="rounded-borders">
                <q-item v-for="(item,index) in info" :key="index" clickable v-ripple>
                    <q-item-section>
                        {{item.label}} ---- {{item.value}}
                    </q-item-section>
                </q-item>
            </q-list>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

/*************data******************** */
let info = ref([
    {label:'name',value:'Brightness'},
])
/***************methods********************* */

/******************events************************* */
</script>

<style scoped>

</style>