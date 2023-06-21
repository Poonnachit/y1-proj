<script setup>
import { reactive, ref } from 'vue'
import axios from 'axios'

const formData = reactive({
  text1: '',
  text2: '',
  text3: '',
  text4: '',
  text5: '',
  text6: ''
})

const response = ref('')

const submitForm = async () => {
  await axios.post('http://127.0.0.1:8000/', { ...formData }).then((res) => {
    response.value = res.data
  })
}
</script>

<template>
  <v-card class="pa-16 ma-10">
    <v-container>
      <v-row>
        <v-col>
          <v-text-field v-model="formData.text1" label="this is text-input 1"></v-text-field>
        </v-col>
        <v-col>
          <v-text-field v-model="formData.text2" label="this is text-input 2"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-text-field v-model="formData.text3" label="this is text-input 3"></v-text-field>
        </v-col>
        <v-col>
          <v-text-field v-model="formData.text4" label="this is text-input 4"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <v-text-field v-model="formData.text5" label="this is text-input 5"></v-text-field>
        </v-col>
        <v-col>
          <v-text-field v-model="formData.text6" label="this is text-input 6"></v-text-field>
        </v-col>
      </v-row>
    </v-container>
    <v-btn @click="submitForm()" block color="green">Submit</v-btn>
    <h3>{{ response }}</h3>
  </v-card>
</template>
