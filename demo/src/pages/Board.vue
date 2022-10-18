<template>
  <div class="row justify-center q-pt-sm">
    <p class="text-h5">画板</p>
  </div>
  <div class="row  justify-center">
    <SignBoard ref="sign_board" :options="options" v-model="value" :isFullScreen="fullScreen"></SignBoard>
  </div>
  <div class="row  justify-center">
    <div class="q-pa-md q-gutter-sm">
        <q-btn color="red" icon="bi-x-circle-fill" label="清空"  @click="canvasClear()"/>
        <q-btn color="primary" icon="bi-save" label="保存"  @click="saveAsImg()"/>
        <!-- <q-btn color="primary" icon="bi-arrows-fullscreen" label="全屏"  @click="changeFullScreen()"/> -->

        <!-- <q-btn color="primary" icon="bi-cloud-download" label="下载"  @click="downloadSignImg()"/> -->
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import SignBoard from "../components/SignBoard/index.vue";

/******************data******************* */
const sign_board = ref(null);
let value = ref(null);
let options = ref({
  isFullScreen: false, ////是否全屏手写 [Boolean] 可选
  isFullCover: false, //是否全屏模式下覆盖所有的元素 [Boolean]   可选
  isDpr: false, //是否使用dpr兼容高分屏 [Boolean] 可选
  lastWriteSpeed: 1, //书写速度 [Number] 可选
  lastWriteWidth: 1, //下笔的宽度 [Number] 可选
  lineCap: "round", //线条的边缘类型 [butt]平直的边缘 [round]圆形线帽 [square]	正方形线帽
  lineJoin: "bevel", //线条交汇时边角的类型  [bevel]创建斜角 [round]创建圆角 [miter]创建尖角。
  canvasWidth: 400, //canvas宽高 [Number] 可选
  canvasHeight: 600, //高度  [Number] 可选
  isShowBorder: true, //是否显示边框 [可选]
  bgColor: "#fcc", //背景色 [String] 可选
  borderWidth: 1, // 网格线宽度  [Number] 可选
  borderColor: "#ff787f", //网格颜色  [String] 可选
  writeWidth: 5, //基础轨迹宽度  [Number] 可选
  maxWriteWidth: 10, // 写字模式最大线宽  [Number] 可选
  minWriteWidth: 1, // 写字模式最小线宽  [Number] 可选
  writeColor: "#101010", // 轨迹颜色  [String] 可选
  isSign: true, //签名模式 [Boolean] 默认为非签名模式,有线框, 当设置为true的时候没有任何线框
  imgType: "png", //下载的图片格式  [String] 可选为 jpeg  canvas本是透明背景的
});
/*****************methods***************** */
/**
 * 清除画板
 */
function canvasClear() {
  sign_board.value.canvasClear();
}
/**
 * 保存图片
 */
function saveAsImg(){
    const img = sign_board.value.saveAsImg();
    alert(`image 的base64：${img}`);
}
/**
 * 下载图片
 */
function downloadSignImg(){
    sign_board.value.downloadSignImg();
}
/**
 * 切换全屏
 */
function changeFullScreen() { 
    options.value.isFullScreen = !options.value.isFullScreen
}

/********************events********************* */
</script>

<style scoped></style>
