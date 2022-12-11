<script setup>
import { ref, computed } from "vue";
import QrcodeVue from "qrcode.vue";

const textcode = ref(null);
const size = 300;

const makeCode = computed(() => {
    if (!textcode.value) {
        return;
    } else {
        return textcode.value;
    }
});
</script>

<template>
    <div class="header">QR Code Genralator</div>
    <div class="qrcode-app">
        <div class="qrcode-input"><input type="text" v-model="textcode" /></div>
        <div class="qrcode-render">
            <qrcode-vue
                class="qrvalue"
                v-if="!!textcode"
                :value="makeCode"
                :size="size"
                background="#FFC533"
            />
            <h3 v-else> QRCode can not be generated for empty string </h3>
        </div>
    </div>
</template>

<style scoped>
.header {
    font-size: 2rem;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 700;
    text-align: center;
    margin: 1rem 0;
}

.qrcode-app {
    background-color: #FFC533;
    width: 380px;
    margin: 30px auto;
    padding: 20px;
    display: grid;
    row-gap: 20px;
    box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.75);
    border-radius: 25px;
    border: 1px solid rgba(0, 0, 0, 0.75);
}

.qrcode-input {
    display: flex;
    justify-content: center;
}
.qrcode-input input {
    width: 300px;
    height: 2rem;
    border: 1px solid #000;
    border-radius: 3px;
    padding: 0 0.5rem;
    font-size: 1rem;
}

.qrcode-render {
    display: flex;
    justify-content: center;
}

.qrcode-render h3 {
  font-size: 1rem;
  font-family: Arial, Helvetica, sans-serif;
  color: red;
  font-weight: 700;
}
.qrvalue {
    width: 300px;
}
</style>
