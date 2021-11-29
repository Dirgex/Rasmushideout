<template>
  <div>
      <button class="close" @click="closeMail()">X</button>
      <p>Thanks for your mail, we will never reply</p>
  </div>
</template>

<script>
export default {
    name: 'Popupcontact',
    methods:{
        closeMail(){
            this.$emit('close-mail');
        }
    }
}
</script>

<style>

</style>