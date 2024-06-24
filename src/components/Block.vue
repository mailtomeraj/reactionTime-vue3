<script setup>
import { onMounted, onUpdated, ref } from 'vue';
const showBlock = ref(false)
const timer= ref(null)
const reactionTime = ref(0)

const props = defineProps({
    delay:Number
})

const emit = defineEmits(["end"])

onMounted(()=>{
  setTimeout(()=>{
    showBlock.value = true;
    startTimer()
  }, props)
})
const startTimer = () => {
  timer.value = setInterval(() => {
    reactionTime.value += 10
  }, 10)
}
const stopTimer = () => {
  clearInterval(timer.value)
  emit('end', reactionTime.value)

}

</script>



<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>



<style>
.block{
    width:400px;
    border-radius: 20px;
    background: #0faf87;
    color: #fff;
    padding: 100px 0;
    margin:40px auto
}
</style>