<template>
  <q-page padding>
    
  
   
    <div class="q-pa-md q-gutter-sm">
 
      {{ counter }}
    <q-btn color="primary" @click="counter++" style="width: 150px">
      Tambah
    </q-btn>
    <br>
      </div>


      <input
        filled
        v-model="message"
        v-autofocus
        @keyup.esc="clearMessage()"
        @keyup.enter="alertMessage()"
        label="Your name *"
        lazy-rules
        ref="messageInput"
        :style="errorStyle"
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />


      <div>
        <q-btn @click="clearMessage()" label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>

    <h5 class="border-gray" v-if="message.length">Pesan anda : {{ message }}</h5>
    <h5 class="border-gray" v-else>Tidak ada pesan</h5>


    <h2>Uppercase</h2>
    <h5 class="border-gray" >Pesan anda : {{ messageUppercase }}</h5>
    <h5 class="border-gray" >Lowercase message: {{ message | messageLowercase }}</h5>
    
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      message: "I love VUE JS",
      counter: 0
    }
  },
  computed: {
    messageUppercase(){
      console.log('ini fungsi uppercase')
      return this.message.toUpperCase()
    },
    errorStyle() {
    if (this.message.length > 2) { // Memastikan this.message ada dan memiliki panjang lebih dari 20
      return {
        'color': 'red',
        'background': 'pink',
      }
    }
    return null;
  }

  },
  methods: {
    clearMessage(){
      this.message = ''
    },
    alertMessage(){
      alert(this.message)
    },
  },
  filters: {
    messageLowercase(value) {
      return value.toLowerCase()
    }
  },
  directives: {
    autofocus:{
      inserted(el){
        el.focus()
      }
    }
  },
  mounted(){
    console.log(this.$refs.messageInput.className ="bg-green")
  },
}
</script>

<style>
.border-gray{
  border: 1px solid grey;
}
input, button{
  font-size: 23px;
}
.error{
  color:red;
  background: pink;
}
</style>