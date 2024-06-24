<script setup>
const props = defineProps({
    header:String,
    text:String,
    theme:Boolean
}
)
const emit = defineEmits(['close'])

const closeModal = () =>
{
    emit("close")
}

</script>

<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale:theme==='sale'}">
            <h1>{{props.header}}</h1>
            <p>{{props.text}}</p>
            </div>
        </div>
</template>



<style>
.modal{
    width:400px;
    padding:20px;
    margin:100px auto;
    background: white;
    border-radius: 10px;
}
.backdrop{
    top:0;
    left:0;
    bottom:0;
    right:0;
    position:fixed;
    background:rgba(0,0,0,0.5);
    width:100%;
    height:100%
}

.modal h1{
    color:#03cfb4;
    border:none;
    padding:0;
    display:flex

}
.sale, .sale h1{
    background: red;
    color:white
}
</style>