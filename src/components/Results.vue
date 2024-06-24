
<script setup>
 import { onMounted, ref } from 'vue';
 const score = defineProps(['score']
 )
const rank = ref(null);


onMounted(() => {
    if(score < 400)
    {
        rank.value="Meraj fastest fingers"
    }
    else if (score.score < 700)
    {
        rank.value ="Rapid reflexes"
    }
    else
    {
         rank.value ="Snail pace...."
    }
})
</script>

<template>
    <div>
        <p>Reaction time - {{score.score}} ms</p>
        <p class="rank">{{rank}}</p>
    </div>
</template>



<style  scoped>

.rank{
    font-size: 1.4em;
    color: #0faf87; 
    font-weight: bold;
}

</style>