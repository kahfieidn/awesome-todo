<template>
  <q-page padding>
    
  
   
    <div class="q-pa-md q-gutter-sm">
 
      {{ counter }}
    <q-btn color="primary" @click="counter++" style="width: 150px">
      Tambah
    </q-btn>
    <br>
      </div>


      <q-input
        filled
        v-model="message"
        @keyup.esc="clearMessage()"
        @keyup.enter="alertMessage()"
        label="Your name *"
        lazy-rules
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
  }
}
</script>

<style>
.border-gray{
  border: 1px solid grey;
}
</style>