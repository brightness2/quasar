<template>
  <div>
    <div class="row justify-center q-pt-sm">
      <p class="text-h5">信息</p>
    </div>
    <div class="q-pa-md" style="max-width: 350px">
      <q-list dense bordered padding class="rounded-borders">
        <q-item v-for="(item, index) in info" :key="index" clickable v-ripple>
          <q-item-section>
            {{ item.label }} ---- {{ item.value }}
          </q-item-section>
        </q-item>
      </q-list>
      <button @click="doget">请求</button>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { Device } from '@capacitor/device';
import {api} from '../boot/axios';
/*************data******************** */
let info = ref([]);

/***************methods********************* */
async function doget() { 
  api.get('api/android.test/upload_file').then(res=>{
    console.log(res);
  }).catch(err=>{
    console.log(err);
  })
}
/******************events************************* */
onMounted(async ()=>{
  Device.getInfo().then(res => {
    console.log(res);
    info.value.push({ label: "型号", value: res.model })
    info.value.push({ label: "制造商", value: res.manufacturer })
  })
})
</script>

<style scoped></style>
